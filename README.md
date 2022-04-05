# oop-petstore-14th


## Pet Service 기동

- 새로운 터미널을 열어 Pet 서비스를 기동한다. (8080)
```
cd pet-domain
mvn spring-boot:run
```
- 새로운 터미널을 열어 pet을 한 마리 등록해 줍니다.

```javasciprt
http :8080/cats name="몽이" energy=1
```

<br>

## Store Service 기동

- 또 다른 터미널을 열어서 Store 서비스를 기동합니다. (8083)
```
cd store-domain
mvn spring-boot:run
```
- 유저를 한 명 등록해 줍니다.

```javascript
http localhost:8083/customers id="park@naver.com" address:='{"zipcode":"123", "detail":"용인"}'
```
![8083 유저 등록](https://user-images.githubusercontent.com/59447401/147196678-eab14a04-e885-4922-8b9c-9d8f3fdb6a9c.png)

<br>

## 입양하기
- store와 pet은 서로 다른 서비스이기 때문에 pet 에 대한 HATEOAS 링크를 통하여 데이터를 참조해야 한다:
```javascript
http :8083/cartItems customer="http://localhost:8083/customers/park@naver.com" pet="http://localhost:8080/cats/1"
```
![8083 입양](https://user-images.githubusercontent.com/59447401/147196784-6281b8a0-822a-47cb-9ef1-7632b2d509be.png)

