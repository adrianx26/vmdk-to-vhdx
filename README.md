# vmdk-to-vhdx
How to convert VMware vmdk files to Hyper-V’s vhdx format

First of all Microsoft Virtual Machine ConverterMicrosofts Virtual Machine Converter 3.1. 

https://www.microsoft.com/en-us/download/details.aspx?id=23300

Update Powershell 5 Management Frameworkto the latest Version otherwise you get an error: “Remove the members that are not valid (‘RootModule’), then try to import the module again.”.

Start powershell with adminstrative permissions, load the module and get a list of the related cmdlets

1
2
PS D:\> Import-Module "C:\Program Files\Microsoft Virtual Machine Converter\MvmcCmdlet.psd1"
PS D:\> get-command -module *mvmc*
Convert to vhdx and disable VMware Tools. Note: Filetype vhdx Requieres a Windows Version >= 8/2012

1
2
ConvertTo-MvmcVirtualHardDisk -SourceLiteralPath “D:\VMs\ToConvert\Disk0.vmdk” -DestinationLiteralPath “E:\ExportToHyperV\Disk0.vhdx” -VhdType DynamicHardDisk -VhdFormat Vhdx
Disable-MvmcSourceVMTools -DestinationLiteralPath “E:\ExportToHyperV\Disk0.vhdx”



https://docs.microsoft.com/en-us/system-center/vmm/vm-convert-vmware?view=sc-vmm-2022


the new convertor https://www.starwindsoftware.com/tmplink/starwindconverter.exe
