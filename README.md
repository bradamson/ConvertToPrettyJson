# ConvertToPrettyJson

Copied and modified from https://github.com/HYHG/scoop/blob/f712773cc256bd8790e4e93d2a44845dd18658fb/lib/json.ps1

I needed a way to convert JSON and prettify it, since ConvertTo-JSON has weird indenting.

Let's test this out.
```
$test = '{"test":{"test":{"test":true}}}' |ConvertFrom-Json

```

Convert with built-in.  Why are there spaces everywhere? Consistency is nice to have.
```
$test|ConvertTo-Json
{
    "test":  {
                 "test":  {
                              "test":  true
                          }
             }
}
```

Convert with 4 spaces (default)
```
$test|ConvertTo-PrettyJson
{
    "test": {
        "test": {
            "test": true
        }
    }
}
```

Convert with tabs
```
$test|ConvertTo-PrettyJson -useTabs $true
{
        "test": {
                "test": {
                        "test": true
                }
        }
}
```

