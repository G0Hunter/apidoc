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
curl --location --request POST "https://{{url}}/{{path}}" \
  --header "Content-Type: application/json" \
  --data "{
	\"method\": \"create\",
	\"model\" : \"userdata\",
	\"data\":{
		\"payway\": \"payeer\",
		\"account\": \"P1234567\",
		\"curr\":	\"USD\",
		\"comment\":\"foo\"	
	}
}
```
