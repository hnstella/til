# @ModelAttribute

@ModelAttribute 는 다른 말로 커맨드오브젝트라고도 불린다.

* 클라이언트가 전달하는 파라미터를 일대일로 전담 프로퍼티에 담아내는 방식이 커맨드 패턴 그 자체이기 떄문

* 클라이언트의 파라미터를 완벽하게 이해하는 자바빈 객체에 @ModelAttribute 란 어노테이션을 붙이면 자동으로 바인딩 해주고 중간 과정은 모두 생략해준다.

```java
@Controller
public class HomeController {
  @RequestMapping(value="/", method=RequestMethod.GET)
  public String home(@ModelAttribute Command command) {
    ...
  }
}
```

## 사용법

1.  전송할 파라미터를 바인딩 할 수 있는 커맨드형 객체를 만든다.
2.  view 의 엘리먼트에 들어가는 파라미터의 name 과 커맨드형 객체의 프로퍼티명을 맞춘다.

```html
<input name="id"/> ---> public void setId(String id)
<input name="pass"/> ---> public void setPass(String pass)
```

### 참고

[@ModelAttribute 와 @SessionAttribute 의 이해와 한계](http://egloos.zum.com/springmvc/v/535572)
