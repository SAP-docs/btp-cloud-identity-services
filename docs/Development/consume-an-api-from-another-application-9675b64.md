<!-- loio9675b64bc8014f4282e49d0cd8ce60fa -->

# Consume an API from Another Application



## Context



## Procedure

1.  Choose the consumer application.

2.  Choose the *Trust* tab.

3.  Under *Application APIs*, choose *Dependencies*.

4.  Enter the required data.

    Choose the provider application and the API the consumer application consumes.




<a name="loio9675b64bc8014f4282e49d0cd8ce60fa__result_g5m_ms3_pwb"/>

## Results

The consumer application can consume the specified API from the provider application. The following is an example of a token with the relevant claims.

```
{
    "ias_apis": [
        "myApi"
    ],   
    "sub": "P123456",
    "mail": "donna.moore@example.com",
    "iss": "https://mytenant.accounts.ondemand.com",
    "last_name": "Moore",
    "aud": "1ab2cd3e-c573-4ad5-9007-28aa4e587a19", 
    "scim_id": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
    "user_uuid": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
    "azp": "e7c7e327-86c0-48a6-af57-a1234b567869",
    "exp": 1676989626,
    "iat": 1676986026,
    "first_name": "Donna",
    "jti": "123a45b6-a99e-47e0-b03d-b8c1304e8b42"
}
```

