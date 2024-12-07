+++
date = '2022-06-20T23:17:51-06:00'
draft = false
title = 'Writing Good Resusable PowerShell Code'
type = 'post'
tags = ["tech", "powershell", "code"]
+++


Creating functions is among the most frequent tasks you will run int, when working with PowerShell long enough. PS Functions serve a fundamental role, as a component that helps us organize and encapsulate our code. Without them, scripts would become overly complex, cluttered with numerous 'if/else' statements or loops or other repetitive code segments.<br />

By using functions, we bundle our PowerShell logic into manageable units that can be invoked as needed. They allow us to pass parameters to modify their behavior and promote code reuse. To me, code reuse is EVERYTHING in every coding lang, adhering to the DRY (Don’t Repeat Yourself) principle.<br />

<b>So here are some tips I wanna share for writing functions in PowerShell.</b>  Some are even useful when <i>not</i> writing functions!<br />



Use '-Confirm' and '-WhatIf' for dry runs and testing of functions, just as you would with CLI sessions in PowerShell.  For recap of these PowerShell switches: the '-WhatIf' switch is you telling PowerShell to show you what your code will do, without actually doing it. Example:<br />

'''Get-ChildItem -Path C:\Temp\CSV_Files\ -File *.csv -Recurse | Remove-Item -WhatIf

In the above example you can see what 'Remove-Item' would have done if you hadn't provided the '-WhatIf' switch.<br />

And you can use the '-Confirm' switch to make PowerShell pause before each and every action, interactively prompting you asking to <b>confirm</b> each action, before moving on to the next action.<br />

'''Get-ChildItem -Path C:\Temp\CSV_Files\ -File *.csv -Recurse | Remove-Item -Confirm

For PS functions, you can only use '-Confirm' and '-WhatIf' when writing <i><b>advanced functions</b></i> in PowerShell.  So let's talk about advanced functions next.<br />

PowerShell offers a great array of features that you can leverage in your functions, almost effortlessly if you write them as <i>advanced functions</i>.

<a href="https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.4&viewFallbackFrom=powershell-6">Advanced parameters in PowerShell</a>