# Marketing External API - TFLI

## Links

[Create Lead](#create-lead)

## <a name="create-lead"></a>Create Lead

**Method: POST**

**Test-URL:** https://staging.greenpoweradvice.co.uk/api/lead/tfli/v1

**Live-URL:** https://www.greenpoweradvice.co.uk/api/lead/tfli/v1

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

**Body**

```JSON
{
  "businessOwner": "Y",
  "energyType": "both",
  "gasSupplier": "BES",
  "electricitySupplier": "BES",
  "businessName": "Geab",
  "businessAddress": "18 School Ln, Liverpool L1 3BT",
  "fullName": "Thomas Dittmer",
  "email": "test@test.com",
  "mobile": "07981231234",
  "timeToCall": "Now"
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

**<a name="timeToCall"></a>Time to Call**

```JSON
[
  "Now",
  "Morning",
  "Afternoon",
  "Evening"
];
```

**Field Rules**
| Field | Required | Rule |
| :----------- | :--------: | -----------: |
| businessOwner | Y | 1 Characters Max |
| energyType | Y | ('electricity', 'gas', 'both') |
| gasSupplier | Y | [Refer to Gas Valid Suppliers](#gas) |
| electricitySupplier | Y | [Refer to Electricity Valid Suppliers](#elec) |
| businessName | Y | 100 Characters Max |
| businessAddress | Y | 255 Characters Max |
| fullName | Y | 120 Characters Max |
| email | Y | 100 Characters Max |
| mobile | Y | 30 Characters Max |
| timeToCall | N | [Refer to Time To Call](#timeToCall) |

#### Status Codes

**Response 201:**

"Successful"

**Response 400:**

!!! Validation errors !!!

mobile:

```JSON
{
    "error": {
        "message": "Invalid Mobile number",
        "body": "Must be a valid mobile phone number regex: /((\\+44(\\s\\(0\\)\\s|\\s0\\s|\\s)?)|0)7\\d{3}(\\s)?\\d{6}/"
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

fullName:

```JSON
{
    "error": {
        "message": "Invalid Full name",
        "body": "Full name has to be 1 - 120 chars"
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

electricitySupplier:

```JSON
{
    "error": {
        "message": "Invalid Electric supplier",
        "body": "Please check API docs"
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

energyType:

```JSON
{
    "error": {
        "message": "Invalid Type of Energy",
        "body": "Has to be ‘Gas', ‘Electric’ or 'Both’"
    }
}
```

businessOwner:

```JSON
{
    "error": {
        "message": "Invalid Business Owner",
        "body": "Has to be ‘Y' or 'N’"
    }
}
```

businessAddress:

```JSON
{
    "error": {
        "message": "Invalid business address",
        "body": "Business name has to be 1 - 255 chars"
    }
}
```

timeToCall:

```JSON
{
    "error": {
        "message": "Invalid Time to Call Value",
        "body": "Please check API docs"
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
