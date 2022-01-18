## Rest API

### Modul utilizator:

1. `POST /user/create`

Parameters:

```
  {email: userEmail
  password: userPassword
  confirmPassword: userConfirmPassword}
  ```

Response:

```
 201: created
 40x: user already exists
 40x: password and confirmPassword doesn't match
 501: internal server error
 ```

2. `PUT /user/modify`

Parameters:

```
  {password: userPassword
  newEmail: userNewEmail}
  ```

Response:

```
20x: modified
40x: incorect password
40x: email already exists
501: internal server error
```

3. `PUT /user/resetPass`

Parameters:

```
  {password: userPassword
  newPassword: userNewPassword}
  ```

Response:

```
 20x: password reseted
 40x: incorrect password
 501: internal server error
 ```

### Modul partajare:

4. `POST /review/create`

Parameters:

```
  {leavingPoint
  arrivingPoint
  transport
  leavingHour
  length:
  levelOfCrowd
  notes
  satisfaction}
  ```

Response:

```
 201: created
 501: internal server error
 ```

5. `PUT /review/modify/{idUser}/{idReview}`

Parameters:

`idReview + /review/create parameters`

Response:

```
 20x: modified
 40x: invalid idReview
 50x: internal server error
 ```
 
6. `GET /review/listAll/{idUser}`

Parameters:

`{idUser}`

Response:

`[{reviewObject}]`

7. `DELETE /review/{idReview}`

Parameters:

`{idReview}`

Response:

```
 20x: deleted
 40x: invalid idReview
 50x: internal server error
 ```
 
### Modul cautare:
8. `GET /list?search={searchParam}`

Parameters:

```
  {keywords
  transportType
  transportNumber}
  ```

Response:

`[{reviewObject}]`
