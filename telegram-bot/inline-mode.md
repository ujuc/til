# Inline mode

## 설정

* BotFather에게 `/setinline`을 날린다.
* `query` 문으로 사용할 명령어를 입력한다. `{명령어} ...` 형식.
* BotFather가 'Success! Inline settings updated.' 라고 하면 설정 끝.

## Request

* 로그를 보고 있으면 Request는 다음과 같은 형태로 들어온다.

```json
{
    "update_id": ,
    "inline_query":
    {
        "id": ,
        "from":
        {
            "id": ,
            "is_bot": ,
            "first_name": ,
            "last_name": ,
            "username": ,
            "language_code": 
        },
        "location":
        {
            "longitude": ,
            "latitude":
        },
        "query": "",
        "offset": ""
    }
}
```

* `location`의 경우, `inliengeo`를 설정하게되면 나오는 것으로 보여진다.


