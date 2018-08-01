# gramway-DI-Framework
어노테이션 기반 MVC DI 프레임워크

v1
- @controller 어노테이션을 붙이면 객체가 컨트롤러로 인식이 되도록 하였습니다.
컨트롤러 인식이 된 객체의 경우, @RequestMapping을 키값으로 하여 Map에 담기고,
요청받은 url과 비교하여 분기 처리 됩니다.

- 컨트롤러 내의 메서드의 파라미터에 @RequestParam 어노테이션이 붙은 경우,
스프링의 기능과 비슷하게 동작하도록 구현하였습니다.
ex)
public String (@RqeustParam("id") String id){}
내부적으로 id = request.getParameter("id") 와 같이 동작합니다.

- 컨트롤러 내의 메서드의 파라미터가 자바빈 규약에 따르는 클래스인 경우,
자동으로 해당 객체를 생성하여 request영역의 해당 값을 가지고,
setter메서드를 실행하여 반환하는 기능을 구현하였습니다.
ex)
public String (UserDto userdto){}
해당 타입이 자바빈 규약에 따르는지 확인 한 후,
내부적으로 userDto = new UserDto(); UserDto.setUserId(request.getParameter("userId")
와 같이 동작합니다.

- 컨트롤러 내부의 메서드의 return type이 String일 경우,
return "redirect:/" 해주면 직접 response 객체를 호출하지않아도,
response.sendRedirect 되도록 구현하였습니다.


v2
- @repository 어노테이션을 붙이면 BeanFactory에 해당 인스턴스가 한번만 생성되서 저장이 되고,
- @Autowired 어노테이션을 필드에 붙이면 해당 필드 값에 BeanFactory에서 해당 인스턴스를 주입해주는 방식으로 구현하였습니다.

v2.1
- BeanFactory 싱글톤 적용, 리플렉션 라이브러리적용, DI부분 확장가능한 구조로 개선
