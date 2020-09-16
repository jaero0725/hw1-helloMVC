
# < MVC 패턴을 이용하여 회원 등록 기능 구현 >  
---
### 회원등록 기능 구현 방법
#### 1) view 부분에서 registerFrom.jsp 에서 회원등록 폼에서 form을 post방식으로 submit 한다.

#### 2) post방식으로 보내진 data는 form의 action 속성을 통해 "/hw1-helloMVC/doRegister" 으로 매핑된다. 

#### 3) controller 부분인 doRegister에서 폼의 데이터를 post형식으로 받게 된다. 

#### 4) CustomerService에서 회원가입관련 메서드를 구현한다.  - 회원등록 로직 

#### 5) CustomerService 객체에서 register 메서드를 통해 Customer 객체를 받아 오면 조건문으로 검사를 하여 어느 페이지로 보낼지 판단.

#### 6) 계정등록이 성공하여 view 부분에서 setAttribute()메서드를 통해 받은 customer객체를 통해 등록된 회원의 정보를 보여준다. 
           
      

    
    
