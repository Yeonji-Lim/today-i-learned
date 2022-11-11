# Validation
서버 API구성의 기본은 Validation을 잘 처리하는 것.

외부에서 어떤 값을 날리든 Validation을 잘 처리하여 서버가 터지는 일이 없도록 유의하자. 

값, 형식, 길이 등의 형식적 Validation은 Controller에서, 

DB에서 검증해야 하는 의미적 Validation은 Provider 혹은 Service에서 처리하면 된다.