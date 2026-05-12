# KhoiOS-v1.0---Windows-11-Pro-Lite-Optimization
Hey guys, I'm an 8th-grade student with a passion for optimizing operating systems. After more than two hours of dissecting the original ISO file of tiny11(25h2), I've completed my first build called KhoiOS.
code
mkdir C:\KhoiOS_Project
mkdir C:\KhoiOS_Mount
dism /Mount-Image /ImageFile:C:\KhoiOS_Project\sources\install.wim /Index:1 /MountDir:C:\KhoiOS_Mount
C:\KhoiOS_Project\sources
cd C:\KhoiOS_Project\sources
Get-ChildItem -Path C:\KhoiOS_Project -Recurse -Filter "install.*"
Get-ChildItem -Path C:\KhoiOS_Project -Recurse | Where-Object {$_.Length -gt 100MB}
dism /Mount-Image /ImageFile:"C:\KhoiOS_Project\sources\install.wim" /Index:1 /MountDir:"C:\KhoiOS_Mount"
Get-ChildItem -Path C:\KhoiOS_Project -Recurse -Filter "install.wim" | Select-Object FullName
if (!(Test-Path "C:\KhoiOS_Mount")) { New-Item -Path "C:\KhoiOS_Mount" -ItemType Directory }
dism /Mount-Image /ImageFile:
dism /Mount-Image /ImageFile:"C:\KhoiOS_Project\KhoiOS_Project\sources\install.wim" /Index:1 /MountDir:"C:\KhoiOS_Mount"
dism /Mount-Image /ImageFile: 
@echo off
title Khoi OS Auto Builder
:: Tu dong tao thu muc
mkdir C:\KhoiOS_Mount >nul 2>&1
echo Dang phau thuat Windows... Vui long doi...
:: Lenh nay se tu tim file install.wim trong cac thu muc long nhau
for /r "C:\KhoiOS_Project" %%f in (install.wim) do (`
    dism /Mount-Image /ImageFile="%%f" /Index:1 /MountDir:"C:\KhoiOS_Mount"`
)
echo Dang xoa rac...
dism /Image:C:\KhoiOS_Mount /Disable-Feature /FeatureName:Printing-PrintToPDFServices-Features
echo Dang dong goi va hoan tat...
dism /Unmount-Image /MountDir:C:\KhoiOS_Mount /Commit
echo XONG ROI KHOI OI! Chuc mung phap su luoi bieng.
pause@echo off
title Khoi OS Auto Builder
:: Tu dong tao thu muc
mkdir C:\KhoiOS_Mount >nul 2>&1
echo Dang phau thuat Windows... Vui long doi...
:: Lenh nay se tu tim file install.wim trong cac thu muc long nhau
for /r "C:\KhoiOS_Project" %%f in (install.wim) do (`
    dism /Mount-Image /ImageFile="%%f" /Index:1 /MountDir:"C:\KhoiOS_Mount"`
)
echo Dang xoa rac...
dism /Image:C:\KhoiOS_Mount /Disable-Feature /FeatureName:Printing-PrintToPDFServices-Features
echo Dang dong goi va hoan tat...
dism /Unmount-Image /MountDir:C:\KhoiOS_Mount /Commit
echo XONG ROI KHOI OI! Chuc mung phap su luoi bieng.
@echo off
title Khoi OS Auto Builder
:: Tu dong tao thu muc
mkdir C:\KhoiOS_Mount >nul 2>&1
echo Dang phau thuat Windows... Vui long doi...
:: Lenh nay se tu tim file install.wim trong cac thu muc long nhau
for /r "C:\KhoiOS_Project" %%f in (install.wim) do (`
    dism /Mount-Image /ImageFile="%%f" /Index:1 /MountDir:"C:\KhoiOS_Mount"`
)
echo Dang xoa rac...
dism /Image:C:\KhoiOS_Mount /Disable-Feature /FeatureName:Printing-PrintToPDFServices-Features
echo Dang dong goi va hoan tat...
dism /Unmount-Image /MountDir:C:\KhoiOS_Mount /Commit
echo XONG ROI KHOI OI! Chuc mung phap su luoi bieng.
$WimPath = (Get-ChildItem -Path "C:\KhoiOS_Project" -Recurse -Filter "install.wim" | Select-Object -First 1).FullName; dism /Mount-Image /ImageFile:"$WimPath" /Index:1 /MountDir:"C:\KhoiOS_Mount"
dism /Mount-Image /ImageFile:"E:\sources\install.wim" /Index:1 /MountDir:"C:\KhoiOS_Mount"
copy "E:\sources\install.wim" "C:\KhoiOS_Project\install.wim"
dism /Mount-Image /ImageFile:"C:\KhoiOS_Project\install.wim" /Index:1 /MountDir:"C:\KhoiOS_Mount"
attrib -r "C:\KhoiOS_Project\install.wim"
dism /Mount-Image /ImageFile:"C:\KhoiOS_Project\install.wim" /Index:1 /MountDir:"C:\KhoiOS_Mount"
# Xóa sạch Appx (bao gồm cả Edge và đống rác Microsoft)
$Apps = Get-AppxProvisionedPackage -Path "C:\KhoiOS_Mount"
foreach ($App in $Apps) {`
    Write-Host "Đang tiễn biệt: $($App.DisplayName)"`
    Remove-AppxProvisionedPackage -Path "C:\KhoiOS_Mount" -PackageName $App.PackageName`
}
# Tắt các tính năng nặng nề (Feature)
$Features = "Printing-PrintToPDFServices-Features", "WorkFolders-Client", "MSRDC-Infrastructure"
foreach ($f in $Features) {`
    dism /Image:C:\KhoiOS_Mount /Disable-Feature /FeatureName:$f`
}
# Xóa sạch Appx (bao gồm cả Edge và đống rác Microsoft)
$Apps = Get-AppxProvisionedPackage -Path "C:\KhoiOS_Mount"
foreach ($App in $Apps) {`
    Write-Host "Đang tiễn biệt: $($App.DisplayName)"`
    Remove-AppxProvisionedPackage -Path "C:\KhoiOS_Mount" -PackageName $App.PackageName`
}
# Tắt các tính năng nặng nề (Feature)
$Features = "Printing-PrintToPDFServices-Features", "WorkFolders-Client", "MSRDC-Infrastructure"
foreach ($f in $Features) {`
    dism /Image:C:\KhoiOS_Mount /Disable-Feature /FeatureName:$f`
}
# Nạp file Registry của bản Win đang mổ
reg load HKLM\Offline_System "C:\KhoiOS_Mount\Windows\System32\config\SYSTEM"
# Tắt SysMain (Dành cho máy dùng SSD đời cũ hoặc HDD cho đỡ lag)
reg add "HKLM\Offline_System\ControlSet001\Services\SysMain" /v Start /t REG_DWORD /d 4 /f
# Tắt Windows Search (Cho ổ cứng bớt quay tít mù)
reg add "HKLM\Offline_System\ControlSet001\Services\WSearch" /v Start /t REG_DWORD /d 4 /f
# Giải phóng bộ nhớ (Unload) sau khi sửa xong
reg unload HKLM\Offline_System
dism /Image:C:\KhoiOS_Mount /Cleanup-Image /StartComponentCleanup /ResetBase
# Nạp file Default User (để bất kỳ ai đăng nhập cũng nhận cấu hình nhẹ này)
reg load HKLM\Offline_User "C:\KhoiOS_Mount\Users\Default\NTUSER.DAT"
# Tắt hiệu ứng Menu, bóng đổ, hiệu ứng cửa sổ (Visual Effects)
reg add "HKLM\Offline_User\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects" /v VisualFXSetting /t REG_DWORD /d 2 /f
reg add "HKLM\Offline_User\Control Panel\Desktop" /v UserPreferencesMask /t REG_BINARY /d 9012028010000000 /f
reg add "HKLM\Offline_User\Control Panel\Desktop\WindowMetrics" /v MinAnimate /t REG_SZ /d 0 /f
# Làm Menu hiện ra ngay lập tức (không đợi 400ms)
reg add "HKLM\Offline_User\Control Panel\Desktop" /v MenuShowDelay /t REG_SZ /d 0 /f
reg unload HKLM\Offline_User
# Liệt kê và xóa các Driver máy in, máy quét thừa thãi (chỉ giữ lại nhân hệ thống)
dism /Image:C:\KhoiOS_Mount /Remove-Driver /Driver:prnms001.inf /Driver:prnms002.inf /Driver:prnms003.inf
# Lưu ý: Lệnh này có thể báo lỗi nếu tên driver khác, nhưng đừng lo, cứ chạy lệnh Cleanup-Image ở bước trước là đã ngon rồi.# Bước 1: Lưu thay đổi
dism /Unmount-Image /MountDir:"C:\KhoiOS_Mount" /Commit
# Bước 2: Nén cực đại (Max Compression) - File install.wim sẽ nhỏ nhất có thể
# Mày chạy lệnh này sau khi Unmount xong nhé
dism /Export-Image /SourceImageFile:"C:\KhoiOS_Project\install.wim" /SourceIndex:1 /DestinationImageFile:"C:\KhoiOS_Project\KhoiOS_Final.wim" /Compress:maxls "C:\KhoiOS_Project\*"
ls "C:\KhoiOS_Project\*"
dism /Export-Image /SourceImageFile:"C:\KhoiOS_Project\install.wim" /SourceIndex:1 /DestinationImageFile:"C:\KhoiOS_Project\KhoiOS_Sieu_Nhe.wim" /Compress:max
dism /Get-WimInfo /WimFile:"C:\KhoiOS_Project\KhoiOS_Final.wim"
dism /Get-WimInfo /WimFile:"C:\KhoiOS_Project\KhoiOS_sieu_nhe.wim" /Index:1
mkdir D:\KhoiOS_Ready
mkdir C:\KhoiOS_Ready
xcopy E:\* C:\KhoiOS_Ready /s /e /f
del C:\KhoiOS_Ready\sources\install.* -Force
Move-Item "C:\KhoiOS_Project\KhoiOS_sieu_nhe.Wim" "C:\KhoiOS_Ready\sources\install.wim" -Force
dir C:\KhoiOS_Project
Move-Item "C:\KhoiOS_Project\install.wim" "C:\KhoiOS_Ready\sources\install.wim" -Force
Start-Process "C:\KhoiOS_Ready\setup.exe"
dism /Get-WimInfo /WimFile:"C:\KhoiOS_Ready\sources\install.wim" /Index:1
dir C:\KhoiOS_Ready\sources\install.wim
# Chạy lệnh đóng gói thư mục thành file ISO
C:\KhoiOS_Ready\sources\oscdimg.exe -n -m -bc:\KhoiOS_Ready\boot\etfsboot.com C:\KhoiOS_Ready C:\KhoiOS_Project\KhoiOS_Final.iso
# Chạy lệnh đóng gói thư mục thành file ISO
C:\KhoiOS_Ready\sources\oscdimg.exe -n -m -bc:\KhoiOS_Ready\boot\etfsboot.com C:\KhoiOS_Ready C:\KhoiOS_Project\KhoiOS_Final.iso
cd C:\
# Xóa thư mục Project cũ
Remove-Item -Path "C:\KhoiOS_Project" -Recurse -Force
Dismount-DiskImage -ImagePath "C:\KhoiOS_Project\tiny11_25H2_Oct25.iso"

