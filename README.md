# VulnDesktopApp

It's similar to DVTA, With less functionality but decided to develop my own app, Gives good feeling about how things actually works, hope to continue developing it.
Developed With Visual Studio 2013 Using C#

In this Vulnerable Application, We will discover together 5 vulnerablilties:-
1. Binary Analysis to find sensitive data.
2. GUI Testing
3. CSV Injection
4. EXE Hijacking
5. DLL Hijacking


### 1. Binary Analysis to find sensitive data.
Open VulnAppDemo.exe, There is a form to login, Where to find creds ?!.
- Use dnSPY to review the source code and get creds.

https://github.com/doosec101/VulnDesktopApp/assets/128431701/c2eaa91c-526b-4397-9678-9d0e55c3b438

### 2. GUI Testing
Open the app, There is a masked password at the bottom, With textBox disabled, How to see the masked password?
- Uncover the masked password with diff tools like Winspy++ , View Wizard.

https://github.com/doosec101/VulnDesktopApp/assets/128431701/c737ef57-a025-409f-b085-c254503ae78f

### 3. CSV Injection
When you enter any Username & Password, The data saved in CSV File called data.csv.
Hmmm can we try CSV Injection?
- The answer is Yes., By putting this payload `=cmd|' /C notepad'!'A1'` as Username || Password , It Opens notepad.

https://github.com/doosec101/VulnDesktopApp/assets/128431701/4a11ef05-1724-47e5-b019-543a489c07f1

### 4. EXE Hijacking

To exploit this you have first to find the right Creds to activate the `Execute` button
After login with righ creds, The `Execute` Button becomes enable, When you enter that button the app searchs for `testcalc.exe` in the $PATH env.
So Can we Hijacking this and gets shell?
- The answer is Yes, Use Procmon.exe to see the dll & exe that the app calls, Then create shell and name it with `testcalc.exe`

See the exploitation video.
https://drive.google.com/file/d/1-55LABj4FN-f3k3HdS5rkuaRS_QK8Xpt/view?usp=sharing

### 5. DLL Hijacking

Same as EXE Hijacking, instead this time we looking for dll files.

https://drive.google.com/file/d/1VLbtvyOAIo0iAH-OnBuEYeVlY1B2M0bv/view?usp=sharing

## References:-
1. https://github.com/RakeshKengale/RaKKeN/blob/master/Index/Thick_Client.md
2. https://infosecwriteups.com/thick-client-pentest-modern-approaches-and-techniques-part-1-7bb0f5f28e8e
3. https://hackerone.com/reports/530292
4. https://hackerone.com/reports/943725
5. https://hackerone.com/reports/583184
6. https://hackerone.com/reports/513154
7. https://hackerone.com/reports/291539

Credit by: doosec101

Hackerone Profile: https://hackerone.com/doosec101

Hope you enjoy it.
