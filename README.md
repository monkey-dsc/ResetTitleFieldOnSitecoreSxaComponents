# Reset Title Field On Sitecore Sxa Components

After an update from Sitecore 10.2.0 to Sitecore 10.3.1 I figured out that the "Title" field of default SXA components have changed.

They appeared in Experience Editor, especially in language versions other than *"en"*. I reported this as a bug *(CS0405766)* they answered to reset those fields manually on each component.

![Components in Sitecore Experience Editor](https://github.com/monkey-dsc/ResetTitleFieldOnSitecoreSxaComponents/blob/master/images/ComponentsInEE.png?raw=true)

But, I searched for that field and more than 60 components was affected! As lazy I am I created a Sitecore PowershellScript for that. 

### Installation

Just create an Item in your Sitecore Powershell Extensions Library, copy and paste the code below into it, save and execute.

```
$itemIds = @(
    "{668126E9-5A1E-4553-974B-A26400B5BAD7}",
    "{2147200A-CD2E-4196-91D5-E23C0724502D}", 
    "{E824F48B-CD60-4773-A82E-4D28B6DBF339}", 
    "{7240053B-9140-48AC-ACEA-ABFCCD7761A1}", 
    "{02F6FB63-FE92-44E8-AFA2-20747C893502}", 
    "{5A236869-E375-49C0-A92D-0C2F1DB7788F}", 
    "{FD8FDB4A-8022-453C-AFF5-8E68D3D3EB5F}", 
    "{B64A5F49-1B79-4F86-AECD-C5A2C0DEFEED}", 
    "{70181515-2AAB-4710-91F4-52A08151693E}", 
    "{99F62656-1F3E-4F98-9EAC-A596FB174BA0}", 
    "{9CE31D9D-E11C-49B8-8A6C-76517F05A055}", 
    "{5F32188E-D73C-47B8-97D4-7097070D8F46}", 
    "{18EE0052-ACCD-42AD-8D80-D60CB88D9950}", 
    "{EC4A491F-CC4B-4175-858A-3E6E859540BB}", 
    "{6DDD6E6E-9B58-45A8-970B-6C7228C62688}", 
    "{EEFF6595-06EB-4138-9201-D59E11E74EBB}", 
    "{4B34F7C7-BA6F-4629-810E-6CA3441F4689}", 
    "{1C9E9ECD-8A44-4E07-A9CD-9E065FBBAD17}", 
    "{17C11A05-1A29-43B9-BD01-D1133A94BA69}", 
    "{84A2E020-6002-46E4-84D8-2383BF061369}", 
    "{02F6FB63-FE92-44E8-AFA2-20747C893502}", 
    "{1B9D1028-C20C-407B-9DCD-AFFE86A6F793}", 
    "{C08B42E9-C147-47D1-B50C-6274EB3A8BAA}", 
    "{D8C26E4E-DC33-48F8-8BD1-379A79EC3259}", 
    "{D8C26E4E-DC33-48F8-8BD1-379A79EC3259}", 
    "{74A012F7-D87B-456E-A447-6F392C69C48F}", 
    "{75797CEC-589F-47E2-B416-45CFF546EEE1}", 
    "{31EB03B0-13E7-4C65-9BC0-0E7887A51B05}", 
    "{EBE4FDEF-16D5-4D19-833C-24A241628A3A}", 
    "{D3BF9175-3C00-4BD5-978B-D27DF8C41482}", 
    "{C4A0614E-5A4A-4ECF-B49B-B0D82E5EEE7E}", 
    "{75562C38-22F6-4B63-AF7A-DAF44F0730F1}", 
    "{4E3A41DD-AFB7-4763-BA20-FF27E0BEEDDF}", 
    "{725A80DD-0CF3-451B-B2DB-220DA5247771}", 
    "{DD05144A-BD66-4EA3-956A-4B7104DAABA3}", 
    "{AA9C8D1C-B210-4EFA-86DB-83E8FA32C672}", 
    "{AB626903-E218-4AB6-8691-DA4982C3548C}", 
    "{87F9B654-5410-4DC2-9C9D-E3B55F623C6C}", 
    "{B8C1A9D2-DE76-4519-AFF4-1442525F32B0}", 
    "{B3635965-6786-457C-9DEE-28DE73C0A331}", 
    "{4B737984-1EAC-4E50-8DD1-883566FA7BDE}", 
    "{2D36CF85-84BE-42D2-B710-8D13B8844CDD}", 
    "{96B0D7F6-FE54-44EA-A6A6-4AE308411488}", 
    "{8C4F99AC-5C29-40EF-9A33-1A4C73DBFEA9}", 
    "{0A5DBE83-3914-4630-90EF-D1BBBCDEDE7F}", 
    "{734F9A5A-C02A-4D34-87E8-29C732D8EB67}", 
    "{38D3DE1F-F23C-4587-AE30-06EC5ED73E82}", 
    "{8A67FCA9-7E15-4B7C-B6B8-86F37CAFE720}", 
    "{42C9489B-01B9-4533-9CAC-1A84A4B4AB65}", 
    "{BEFC61BF-8CFD-4478-9F5C-8422E6E2F005}", 
    "{11E20569-CC3A-4C0F-B068-50605C3C3AA7}", 
    "{6D6E0783-1423-4834-AB27-74312E8B6754}", 
    "{AE5D211A-4FF1-4E9E-BA0F-9442B0ABCA91}", 
    "{29AC186D-0A90-470F-93D0-F548179B1FC3}", 
    "{BF7F1D61-2F56-45AC-90DE-3BFFBB897E5B}", 
    "{94DB1E7D-B26A-400E-95D6-9186E9AC7394}", 
    "{F1B4CEC1-36B7-4A29-8A14-E7034E70F036}", 
    "{6F0451F9-BF0E-4420-AD61-82BB14A257F9}", 
    "{4F892959-FDE6-4020-8569-2CF934BA412C}", 
    "{F3B01C7D-BD46-4972-AB13-4C9C95C4F23D}", 
    "{C95B7BAD-FA93-41F0-82DE-C2C2BF0A0E89}", 
    "{73A7C430-816E-4481-B4C1-3AB8C2C1052B}", 
    "{2C054663-0478-41FF-8F50-5D5D69CBA936}", 
    "{6E6C0B3C-7041-4FFA-B0FC-849D1975D368}", 
    "{C28B5524-3740-4DC2-B5BF-9CF7B6434A19}", 
    "{2F325664-BBA1-4EAC-8D8F-C365D2F40245}", 
    "{BBC2E73A-DE40-493B-9320-86D66D024AAF}", 
    "{B31A3B74-D75C-477A-BE16-F44C4593DFE9}", 
    "{FEFB37DF-0883-4714-B7FC-607B5ADA8908}", 
    "{AE1EB2D8-3A7C-4337-83DF-1B0B0C857BEE}", 
    "{FFDB9651-779B-4219-B983-D42FEF761E1B}", 
    "{3C9E33F5-955F-4E70-935F-4B8A07869419}", 
    "{B07D518C-4E73-45EF-B478-DEAE9EC7426F}", 
    "{B07D518C-4E73-45EF-B478-DEAE9EC7426F}"
)

foreach ($itemId in $itemIds) {
    
    Get-Item -Path "master:" -ID $itemId -Version * -Language * | Reset-ItemField -Name 'Title'
    Write-Host ("The field 'Title' was resetted for the item ID {0}." -f $itemId)
}
```

As I mentioned this may not happen for "en" language. ButI saw this will affect Dansk and all other languages as well.