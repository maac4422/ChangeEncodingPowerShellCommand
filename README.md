# ChangeEncodingPowerShellCommand
This is a power shell command recursive to change encoding at files inside a directory

$PSDefaultParameterValues['Out-File:Encoding'] = 'ascii';
Get-ChildItem *.* -recurse -force| % { Get-Content $_ | Out-File -FilePath "$($_.DirectoryName)\1-$($_.name)" -Encoding default } ; 
Get-ChildItem *.*   -exclude 1-*  -recurse -force | foreach ($_) {Remove-Item $_.fullname -force}; 
Get-ChildItem *.*  -recurse -force | Rename-Item -NewName{$_.name -replace "1-",""} -force
