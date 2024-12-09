+++
date = '2021-05-22T23:17:51-06:00'
draft = false
title = 'Log Your Scripts! Pt 2 - Live Use-Case'
type = 'post'
tags = ["tech", "devops", "endpoint-mgmt", "powershell", "code", "fundamentals", "best-practice"]
+++

The other day <a href="http://julianwest.me/Blog/logyourps-scripts/">I posted a quick primer</a> on logging in our PS scripts.  Here I will expand on that, with a use-case example I just wrote code for yesterday. Here is a registry-reading function I bashed together, as but one example of something I needed to accomplish in reading in a setting and logging it.  Thus allowing me to keep a thorough, auditable record of registry changes during an automation task.

## Reading Registry Values with <span class="mono">Get-RegistryValue</span>

For many automation tasks, you’ll need to retrieve configurations from the Windows Registry. The Get-RegistryValue function allows you to read a specific property from the Registry without cluttering your code. Errors are cleanly handled (returning $false if a value can’t be found), making it easy to integrate error-checking and logging.

~~~
Function Get-RegistryValue($RegPath, $Property) {
    Try {
        $Item = Get-ItemProperty -Path $RegPath -Name $Property -ErrorAction Stop
        $ItemProperty = $Item | Select -ExpandProperty $Property
        Return $ItemProperty
    }
    Catch {
        Return $false
    }
}
 ~~~

And here's a recap of the Writelog function <a href="http://julianwest.me/Blog/logyourps-scripts/">I wrote about the other day</a>:

~~~
Function WriteLog($LogString) {
    ##########################################################################
    ## Writes a timestamped entry to a log file defined by $LogFile variable
    ##########################################################################

    $Stamp = (Get-Date).ToString("yyyy/MM/dd HH:mm:ss")
    $LogMessage = "$Stamp $LogString"
    Add-Content $LogFile -Value $LogMessage
}
~~~

**Example Usage**:

~~~
$SomeValue = Get-RegistryValue 'HKLM:\SOFTWARE\MyApp' 'InstallPath'

If ($SomeValue) {
    WriteLog "Successfully retrieved InstallPath value: $SomeValue"
} Else {
    WriteLog "Failed to retrieve InstallPath from registry."
}
~~~

You should log <i>everything</i> you're reading-in, or changes you're making (files written, etc) during any scheduled or automated run of your PS scripts.  This example shows a combination of <span class="mono">Get-RegistryValue</span> and <i>WriteLog function</i> to demonstrate a use-case, and the benefit becomes obvious once you make this a coding practice: you can retrieve configurations, make decisions based on those values, and log both the successes and failures in a neatly timestamped manner. <br />

Happy scripting...