# Marketing External API - MIGHTY

## Links

[Create Lead](#create-lead)

[Field Rules](#field-rules)

## <a name="create-lead"></a>Create Lead

**Method: POST**

**Test-URL:** https://staging.greenpoweradvice.co.uk/api/lead/mighty/v1

**Live-URL:** https://www.greenpoweradvice.co.uk/api/lead/mighty/v1

**URL Params:**

```JSON
N/A
```

**URL Query Params:**

```JSON
N/A
```

**Headers:**

```JSON
token: 123456789
```

**Body Full**

```JSON
{
    "energyType": "Both",
    "gasSupplier": "British Gas",
    "electricitySupplier": "-none-",
    "businessName": "Utility Locker",
    "street": "18 School Ln",
    "postcode": "L13BT",
    "city": "Liverpool",
    "fullName": "Thomas Dittmer",
    "email": "shuanking678@test.com",
    "mobile": "07981231234",
    "phone": "01514442222",
    "gasRenewalDate": "10-2021",
    "electricityRenewalDate": "10-2021",
    "gasSpend": "3000",
    "electricitySpend": "3000",
    "notes": "test note"
}
```

**Body partial**

```JSON
{
    "energyType": "Both",
    "gasSupplier": "British Gas",
    "electricitySupplier": "-none-",
    "businessName": "Utility Locker",
    "street": "18 School Ln",
    "postcode": "L13BT",
    "city": "Liverpool",
    "fullName": "Thomas Dittmer",
    "email": "shuanking678@test.com",
    "mobile": "07981231234"
}
```

#### Valid Suppliers

**<a name="gas"></a>gas**

```JSON
[
  "-None-",
  "Dual",
  "Crown Gas & Power",
  "GDF Suez",
  "BES",
  "Axis",
  "British Gas Business",
  "CNG",
  "Corona Energy",
  "Dong Energy/Orsted",
  "E.ON",
  "Ecotricity",
  "EDF",
  "Enterprise Gas",
  "Extra Energy",
  "First Utility",
  "Gazprom Energy",
  "Good Energy",
  "Haven Power",
  "Hudson Energy",
  "LoCO2 Energy",
  "N-Power",
  "Opus Energy",
  "Ovo Energy",
  "Regent Gas",
  "Scottish Power",
  "SmartestEnergy",
  "SSE",
  "Total Gas & Power",
  "United Gas & Power",
  "WINGAS",
  "Yorkshire Gas & Power",
  "Yu Energy",
  "Utility Warehouse",
  "BG Corp.",
  "BG SME",
  "Scottish Gas",
  "One Energy",
  "NEPO",
  "Economy Gas Ltd",
  "D-Energi",
  "ME Energy",
  "The Gas Company",
  "Utilita",
  "Prime Gas and Power",
  "Solarplicity",
  "PFP Energy",
  "Valda Energy",
];
```

**<a name="elec"></a>elec**

```JSON
[
  "-None-",
  "Axis",
  "BES",
  "BG Corp",
  "BG SME",
  "British Gas Business",
  "CNG",
  "Corona Energy",
  "Crown Gas & Power",
  "Dong Energy/Orsted",
  "Dual",
  "E.ON",
  "Ecotricity",
  "EDF",
  "Enterprise Gas",
  "Extra Energy",
  "First Utility",
  "Gazprom Energy",
  "GDF Suez",
  "Good Energy",
  "Haven Power",
  "Hudson Energy",
  "LoCO2 Energy",
  "N-Power",
  "Opus Energy",
  "Ovo Energy",
  "Regent Gas",
  "Scottish Power",
  "SmartestEnergy",
  "SSE",
  "Total Gas & Power",
  "United Gas & Power",
  "Utility Warehouse",
  "WINGAS",
  "Yorkshire Gas & Power",
  "Yu Energy",
  "One Energy",
  "NEPO",
  "D-Energi",
  "Unicom",
  "The Gas Company",
  "Utilita",
  "Western Power",
  "F&S Energy",
  "Npower Corp.",
  "Prime Gas and Power",
  "Solarplicity",
  "PFP Energy",
  "Valda Energy",
  "Bryt Energy",
];
```

## <a name="field-rules"></a>Field Rules

<!-- **Field Rules** -->

| Field                  | Required |                                                              Rule |
| :--------------------- | :------: | ----------------------------------------------------------------: |
| businessOwner          |    Y     |                                                  1 Characters Max |
| energyType             |    Y     |                                    ('electricity', 'gas', 'both') |
| gasSupplier            |    Y     |                              [Refer to Gas Valid Suppliers](#gas) |
| electricitySupplier    |    Y     |                     [Refer to Electricity Valid Suppliers](#elec) |
| businessName           |    Y     |                                                100 Characters Max |
| businessAddress        |    Y     |                                                255 Characters Max |
| fullName               |    Y     |                                                120 Characters Max |
| email                  |    N     |                                                100 Characters Max |
| mobile                 |    N     |   30 Characters Max && at least phone or mobile must be populated |
| phone                  |    N     |                                                 30 Characters Max |
| gasRenewalDate         |    N     |                                7 Characters Max format('MM-YYYY') |
| electricityRenewalDate |    N     |                                7 Characters Max format('MM-YYYY') |
| gasSpend               |    N     |                                                 13 Characters Max |
| electricitySpend       |    N     |                                                 13 Characters Max |
| notes                  |    N     | 64kb Characters Max around 64000 characters depending on encoding |

#### Status Codes

**Response 201:** No response given

**Response 400:**

!!! Validation errors !!!

energyType:

```JSON
{
    "error": {
        "message": "Invalid Type of Energy",
        "body": "Has to be ‘Gas', ‘Electric’ or 'Both’"
    }
}
```

gasSupplier:

```JSON
{
    "error": {
        "message": "Invalid Gas supplier",
        "body": "Please check API docs"
    }
}
```

electricitySupplier:

```JSON
{
    "error": {
        "message": "Invalid Electric supplier",
        "body": "Please check API docs"
    }
}
```

businessName:

```JSON
{
    "error": {
        "message": "Invalid business name",
        "body": "Business name has to be 1 - 100 chars"
    }
}
```

street:

```JSON
{
    "error": {
        "message": "Invalid street",
        "body": "street has to be 1 - 255 chars"
    }
}
```

postcode:

```JSON
{
    "error": {
        "message": "Invalid Postcode",
        "body": "please provide a valid postcode Regex: /\\b((?:(?:gir)|(?:[a-pr-uwyz])(?:(?:[0-9](?:[a-hjkpstuw]|[0-9])?)|(?:[a-hk-y][0-9](?:[0-9]|[abehmnprv-y])?))))([0-9][abd-hjlnp-uw-z]{2})\\b/i"
    }
}
```

city:

```JSON
{
    "error": {
        "message": "Invalid city",
        "body": "City has to be 1 - 255 chars"
    }
}
```

fullname:

```JSON
{
    "error": {
        "message": "Invalid Full name",
        "body": "Full name has to be 1 - 120 chars"
    }
}
```

email:

```JSON
{
    "error": {
        "message": "Invalid Email",
        "body": "Must be a valid email regex: /(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|\"(?:[\\x01-\\x08\\x0b\\x0c\\x0e-\\x1f\\x21\\x23-\\x5b\\x5d-\\x7f]|\\\\[\\x01-\\x09\\x0b\\x0c\\x0e-\\x7f])*\")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\\[(?:(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9]))\\.){3}(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9])|[a-z0-9-]*[a-z0-9]:(?:[\\x01-\\x08\\x0b\\x0c\\x0e-\\x1f\\x21-\\x5a\\x53-\\x7f]|\\\\[\\x01-\\x09\\x0b\\x0c\\x0e-\\x7f])+)\\])/"
    }
}
```

mobile:

```JSON
{
    "error": {
        "message": "Invalid Mobile number",
        "body": "Must be a valid mobile phone number regex: /((\\+44(\\s\\(0\\)\\s|\\s0\\s|\\s)?)|0)7\\d{3}(\\s)?\\d{6}/"
    }
}
```

phone:

```JSON
{
    "error": {
        "message": "Invalid phone number",
        "body": "Must be a valid phone number regex: /^((^0)|(^\\+44))(([1x])([0-9x]){8,9}|([2-3x]){10}|(8((00|45)([0-9x]){4}|([0-9x]){9}))$)/"
    }
}
```

mobile && phone empty:

```JSON
{
    "error": {
        "message": "Invalid Phone & Mobile Number",
        "body": "Both Mobile or Phone cannot be empty. You must provide at least one form of contact"
    }
}
```

gasRenewalDate:

```JSON
{
    "error": {
        "message": "Invalid Gas Renewal Date",
        "body": "Gas Renewal Date format MM-YYYY"
    }
}
```

electricityRenewalDate:

```JSON
{
    "error": {
        "message": "Invalid Electricity Renewal Date",
        "body": "Electricity Renewal Date format incorrect  MM-YYYY"
    }
}
```

gasSpend:

```JSON
{
    "error": {
        "message": "Invalid Gas Spend",
        "body": "Gas Spend has must be a decimal 1.00"
    }
}
```

electricitySpend

```JSON
{
    "error": {
        "message": "Invalid Electricity Spend",
        "body": "Electricity Spend has must be a decimal 1.00"
    }
}
```

**Response 403:**

```JSON
{
    "error": {
        "message": "INVALID Token",
        "body": "Please check you are using the correct token"
    }
}
```

**Response 404:**

```JSON
{
    "error": {
        "message": "Not found",
        "body": "URL not Found"
    }
}
```

**Response 405:**

```JSON
{
    "error": {
        "message": "Method Not Allowed",
        "body": "This endpoint does not support {METHOD} method requests"
    }
}
```

**Response 500:**

```JSON
{
  "error": "Internal server error"
}
```
