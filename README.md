# zatca
![](https://img.shields.io/gem/v/zatca) ![](https://img.shields.io/github/workflow/status/mrsool/zatca/Ruby)

A Ruby library for generating QR Codes for the e-invoice standard by ZATCA in Saudi Arabia.

✅ Validated to have the same output as [ZATCA's SDK](https://zatca.gov.sa/en/E-Invoicing/SystemsDevelopers/ComplianceEnablementToolbox/Pages/DownloadSDK.aspx) as of 12 November 2021.

# Installation

## Rubygems
```sh
gem install zatca
```

## Bundler
```sh
bundle add zatca
```

# Usage

```rb
require "zatca"

tags = {
  seller_name: "Mrsool",
  vat_registration_number: "310228833400003",
  timestamp: "2021-10-20T19:29:32+03:00",
  vat_total: "15",
  invoice_total: "115",
  digital_signature: "1234",
  public_key: "145345",
  certificate_signature: "3452345"
}

ZATCA.render_qr_code(tags)
# => data:image/png;base64,...
# Hint (Try pasting the above into your web browser's address bar)
```

If you'd like to customize the size of the QR Code you can manually use the generator like so:

```rb
require "zatca"

tags = ZATCA::Tags.new({
  seller_name: "Mrsool",
  vat_registration_number: "310228833400003",
  timestamp: "2021-10-20T19:29:32+03:00",
  vat_total: "15",
  invoice_total: "115",
  digital_signature: "1234",
  public_key: "145345",
  certificate_signature: "3452345"
})

generator = ZATCA::QRCodeGenerator.new(tags)
generator.render(size: 512)
```
