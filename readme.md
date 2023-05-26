# Description Language

The description language for primary and fallback authentication methods, SSO, and other settings is shown in the listing.  

* Lines 2-4: website description
* Lines 5-9: primary authentication methods
* Lines 10-14: fallback authentication methods
* Lines 15-20: SSO
* Lines 21-25: PII (optional)


``` 
{
        "name": "$name",
        "url": "$url",
        "accountType": "$accounttype",
        "primaryAuthentication":
        {
            "types_possible": [$methods],
            "required": [$logicalmethods]
        },
        "fallbackAuthentication":
        {
            "types_possible": [$methods],
            "required": [$logicalmethods],
        },
        "sso":
        {
            "identity provider": boolean,
            "providers": [$providers],
            "data": [$data]
        }
        "pii":
        {
            "required": [$requireddata],
            "optional": [$optionaldata]
        }
    }
}
```
