New-SelfSignedCertificate -NotBefore (Get-Date) -NotAfter (Get-Date).AddYears(5) `
-Subject "CN=localhost" -KeyAlgorithm "RSA" -KeyLength 2048 `
-HashAlgorithm "SHA256" -CertStoreLocation "Cert:\CurrentUser\My" `
-FriendlyName "HTTPS Development Certificate" `
-TextExtension @("2.5.29.19={text}","2.5.29.17={text}DNS=localhost")
$pwd = convertTo-SecureString -String "PassfN2" -Force -AsPlainText