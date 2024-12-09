+++
date = '2020-05-22T23:17:51-06:00'
draft = false
title = 'Log Your Scripts Pt 2 - A Registry Use-Case'
type = 'post'
tags = ["tech", "devops", "endpoint-mgmt", "powershell", "code", "fundamentals", "best-practice"]
+++

The other day I posted a quick primer on logging in our PS scripts.  Here I will expand on that, with a use-case example I just wrote code for yesterday. Here is a helpful registry-reading function, allowing you to keep a thorough, auditable record of registry changes during an automation task. <br />

## Reading Registry Values with <span class="mono">Get-RegistryValue</span>

For many automation tasks, you’ll need to retrieve configurations from the Windows Registry. The Get-RegistryValue function allows you to read a specific property from the Registry without cluttering your code. Errors are cleanly handled (returning $false if a value can’t be found), making it easy to integrate error-checking and logging.

<div class="code-block">
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
</div>

And here's a recap of the Writelog function I wrote about the other day: <br />

<div class="code-block">
Function WriteLog($LogString) {
    ##########################################################################
    ## Writes a timestamped entry to a log file defined by $LogFile variable
    ##########################################################################

    $Stamp = (Get-Date).ToString("yyyy/MM/dd HH:mm:ss")
    $LogMessage = "$Stamp $LogString"
    Add-Content $LogFile -Value $LogMessage
}
</div>

**Example Usage**: <br />

<div class="code-block">
$SomeValue = Get-RegistryValue 'HKLM:\SOFTWARE\MyApp' 'InstallPath'

If ($SomeValue) {
    WriteLog "Successfully retrieved InstallPath value: $SomeValue"
} Else {
    WriteLog "Failed to retrieve InstallPath from registry."
}
</div>

You should log everything you're doing your PS script, and this example shows a combination of <span class="mono">Get-RegistryValue</span> and <i>WriteLog function</i> to demonstrate the benefits. You can retrieve configurations, make decisions based on those values, and log both the successes and failures in a neatly timestamped manner.