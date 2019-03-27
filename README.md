# API CORE DOCUMENTATION

## Userdata
Используется для хранения данных пользовательей для телеграм-бота. Содержит `ID` пользователя, платежный метод, аккаунт ползователя во внешней платежной системе, валюту и комментарий.

### `POST` userdata validate

```https://{{url}}/{{path}}```

Метод вызывается для проверки данных плательщика и плаежной системы.

Метод метод проверяет валидность переданных данных `(account)` в соответствии форматом переданного аккаунта платежной системы `(payway)`. В случае если проверка не пройдена - вызывается ошибка `App.E.InvalidField('payee')`.

Принимает параметры :

Параметр  | Тип | Обязателен | Описание
------------- | ------------- | ------------- | -------------
payway	| string| 	да|	имя платежной системы
account	| string|	да|	имя аккаунта плательщика в payway
curr	|string	|нет|	название валюты

### BODY

``` python
{
	"method": "validate",
	"model" : "userdata",
	"data": {
		"payway": "payeer",
		"account": "P1234567"
	} 
} 
```

### Example request

``` python
import requests
url = 'https://{{url}}/{{path}}'
payload = "{\n\t\"method\": \"set_promo\",\n\t\"model\" : \"account\",\n\t\"data\" : {\n\t\t\"promo\":{{promo_name}}\n\t}\n}"
headers = {
  'Content-Type': 'application/json'
}
response = requests.request('POST', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```
