# hw1-helloMVC - 1514043_최재호
# < MVC 패턴을 이용하여 회원 등록 기능 구현 >
* 회원등록 기능 구현 방법

1) view 부분에서 registerFrom.jsp 에서 회원등록 폼에서 form을 post방식으로 submit 한다.

2) post방식으로 보내진 data는 form의 action 속성을 통해 "/hw1-helloMVC/doRegister" 으로 매핑된다. 

3) controller 부분인 doRegister에서 폼의 데이터를 post형식으로 받게 된다. 

  - post방식으로 받기 때문에 한글을 처리 할 수 있도록 코드를 추가 해준다. 
  
    request.setCharacterEncoding("utf-8");
  
  - form으로 넘어온 데이터를 모두 request객체의 getParameter() 메서드를 통해 받아준다. 
  
    String id = request.getParameter("id");
		String password = request.getParameter("password");
		String gender = request.getParameter("gender");
		String name = request.getParameter("name");
		String email = request.getParameter("email");
    
 4) CustomerService에서 회원가입관련 메서드를 구현한다.  - 회원등록 로직 
 
  - CustomerService 객체를 singleton pattern으로 받아온다. 
  
  - CustomerService 객체에서 회원등록을 할 수 있는 Register 메서드를 구현한다. 
      
      //addCustomer 메서드
      //customers map 자료구조에 id를 key를 가지는 customer 객체를 삽입해준다. 
      public void addCustomer(Customer customer) {
	    	customers.put(customer.getId(), customer);
	    }
      
       //Register 메서드
       //id , password, name , gender, email 인자들을 모두 받아 Customer객체를 생성하고 addCustomer 메서드를 통해 map에 삽입하고 customer를 리턴해준다. 
       public Customer register(String id, String password, String name, String gender, String email) {
        Customer customer = new Customer(id, password, name, gender, email);
        addCustomer(customer);
        return customer;
      }
      
  5) CustomerService 객체에서 register 메서드를 통해 Customer 객체를 받아 오면 조건문으로 검사를 해서 registerSuccess.jsp로 보낼지, error.jsp 페이지로 보낼지 판단을 한다. 

      String page;
      
      //한 부분이라도 공백이 있으면 에러페이지로 매핑한다. 
      if(id== null|| password == null || gender == null ||name == null || email == null ) {
        System.out.println("계정등록 실패");
        page ="/view/error.jsp";
      }
      
      else {
        System.out.println("계정등록 성공");
        page ="/view/registerSuccess.jsp";
        request.setAttribute("customer", customer);
      }
     
  - 계정등록이 성공하면 request.setAttribute("customer", customer); 를 통해 customer 객체를 페이지에 보내준다. 
      
  6) 계정등록이 성공하여 view 부분에서 setAttribute()메서드를 통해 받은 customer객체를 통해 등록된 회원의 정보를 보여준다. 
           
      

    
    
