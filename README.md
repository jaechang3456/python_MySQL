# python_MySQL

### 1. python MySQL라이브러리 (설치 방법, 임포트 방법 등)
- 파이썬에서 MySQL과 연동하려면 라이브러리가 필요하다. 아래와 같이 설치할 수 있다.
- pip install mysql-connector-python
- 파이썬에 MySQL라이브러리가 설치가 되었다면, 아래와 같이 임포트 한다.
- import mysql.connector

### 2. python에서 MySQL커넥션 하는 방법 (전용 DB 유저 생성 포함)
- python에서 MySQL과 연동하기 전에, 특정 DB에만 접속 할 수 있는 계정을 만들어준다.
- 특정 DB에만 접속 할 수 있는 계정은 MySQL에서 다음과 같이 만다.
- create user 'user_name'@'%' identified by 'user_password';
- 특정 DB에만 접속 할 수 있는 계정을 만들었다면, DB를 관리 할 수 있는 권한을 부여한다. 아래와 같이 한다.
- grant all on DB_name * to 'user_name'@'%'
- 특정 DB에만 접속 할 수 있는 계정과, 관리할 수 있는 권한을 부여 했다면 연동이 가능하다. Python과 MySQL의 연동 순서는 다음과 같다.
- 1. 커넥터로 부터 커넥션을 받는다.             connection = mysql.connector.connect(
                host = 'DB_URL',
                database = 'DB_NAME',
                user = 'streamlit',
                password = 'USER_PASSWORD'
            )
- 2. 커서를 가져온다. cursor = connection.cursor()
- 3. 쿼리문을 작성하여 실행 가능하다.   query = '''insert into TABLE (COLUMNS, COLUMNS, ...)
                        values (%s, %s, ...);'''

                record = (var1, var2, ...)
                
- 4. 적용 및 저장 시켜준다.
- execute : 적용
- commit : 저장

                cursor.execute(query, record)
                connection.commit()
                
- 5. 몇개의 컬럼에 적용 되었는지 확인한다.                
- cursor.rowcount
             
- 6. 모든 데이터베이스 실행 명령을 전부 끝냈으면, 커서와 커넥션을 모두 닫아준다.

            cursor.close()
            connection.close()
            
- 7. 커넥션 코드 예시

 ![캡처](https://user-images.githubusercontent.com/78472987/111598487-9f664280-8812-11eb-88b7-4bcdb85dbe53.PNG)

            
### 3. Python에서 MySQL에 데이터 인서트 하는 방법(변수처리, 1행, 여러행)
- 1. 변수 없이 한 행을 인서트 하는 방법

![변수 x](https://user-images.githubusercontent.com/78472987/111599118-4b0f9280-8813-11eb-82ce-a3be356cf2eb.PNG)

- 2. 한 행을 변수 처리 하여 인서트 하는 방법

![변수처리](https://user-images.githubusercontent.com/78472987/111599179-5b277200-8813-11eb-90ea-13d4cdfd24c5.PNG)

- 3. 여러행을 한번에 인서트 하는 방법

![여러행 처리](https://user-images.githubusercontent.com/78472987/111599232-68dcf780-8813-11eb-8a87-047de3567dad.PNG)

- 4. 날짜와 시간에 관련된 데이터 등을 인서트 하는 방법

![시간 관련](https://user-images.githubusercontent.com/78472987/111599297-7abe9a80-8813-11eb-87b3-b58db3a9fde2.PNG)



