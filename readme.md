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

## Examples

### Google (simplified)



```
{
        "name": "google.com",
        "url": "https://www.google.com",
        "accountType": "identity provider",
        "primaryAuthentication":
        {
            "types_possible": ["password", "totp", "sms"],
            "required":
            "AND",
                {"password": ""},
                ["OR",
                    {"totp": ""},
                    {"sms": ""}
                ]
            ]
        },
        "fallbackAuthentication":
        {
            "types_possible": ["email", "sms", "question"],
            "required":
            ["OR",
                {"email": ""},
                {"sms": ""}
            ]
        },
        "sso":
        {
            "identity provider": true,
            "providers": [],
            "data": []
        }
    }
}
```

### Overleaf

```
{
        "name": "overleaf.com",
        "url": "https://www.overleaf.com",
        "accountType": "sensitive account",
        "primaryAuthentication":
        {
            "types_possible": ["password", "sso"],
            "required":
            ["OR",
                {"password": ""},
                {"sso": ""}
            ]
        },
        "fallbackAuthentication":
        {
            "types_possible": ["email"],
            "required": {"email": "multiple"},
        },
        "sso":
        {
            "identity provider": false,
            "providers": ["google.com", "orcid.org", "twitter.com", "ieee.org", "institutional"],
            "data": ["identifier"]
        }
    }
}
```