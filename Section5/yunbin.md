# 회원 관리 예제 - 웹 MVC 개발 

- 회원 웹기능 -홈 화면 추가
- 회원 웹기능 -등록
- 회원 웹 기능 -조회



## 회원 웹 기능 - 홈 화면 추가



**홈 컨트롤러 추가** 

controller/HomeController

```java
package hello.hellospring.controller;


import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/")
    public String home(){
        return "home";
    }
}
```

**회원 관리용 홈** 

resources/templates/home.html

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div class="container">
    <div>
        <h1> Hello Spring</h1>
        <p>회원 기능</p>
        <p>
            <a href="/members/new">회원 가입</a>
            <a href="/members">회원 목록</a>
        </p>

    </div>
</div>

</body>
</html>
```



## 회원 웹 기능 - 등록



## 회원 등록 폼 개발 



**회원 등록 폼 컨트롤러** 

```java
package hello.hellospring.controller;

import hello.hellospring.domain.Member;
import hello.hellospring.service.MemberService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;

@Controller
public class MemberController {

    // private final MemberService memberService = new MemberService(); new로 여러개 만들 필요가 없다 하나만 만들면 되지
    // cmd + N > Constructor 선택
    private final MemberService memberService;

    @Autowired //스프링 컨테이너 등록
    public MemberController(MemberService memberService) {
        this.memberService = memberService;
    }

    @GetMapping("members/new") //get
    public String createForm(){
        return "members/craeteMemberForm"; //templates 랜더링
    }

    @PostMapping("/members/new") //post 매핑
    public String create(MemberForm form){
        Member member = new Member();
        member.setName(form.getName());

        memberService.join(member);

        return "redirect:/";
    }
}
```

**회원 등록 폼 HTML**

resources/templates/members/createMemberForm.html

```html
<!DOCTYPE html>
<html lang="en">
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div class="container">
  <form action="/members/new" method="post">
    <div class="form-group">
      <label for="name">이름</label>
      <input type="text" id="name" name="name" placeholder="이름을 입력하세요">
    </div>
    <button type="submit">등록</button>
  </form>
</div>
</body>
</html>
```



## 회원 웹 기능 -조회

MemberController

```java
@GetMapping("/members")
public String list(Model model){
    List<Member> members = memberService.findMembers();
    model.addAttribute("members",members); //list로 모든회원 담아놓음
    return "members/memberList";
}
```



회원조회 

members/memberList.html

```html
<!DOCTYPE html>
<html lang="en">
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
 <div class="container">
    <table> 
        <thead>
        <tr>
            <th>#</th>
            <th>이름</th>
        </thead>
        <tbody>
        <!-- for each 돌려서 줌 -->
        <tr th:each="member : ${members}">
            <td th:text="${member.id}"></td>
            <td th:text="${member.name}"></td>
        </tr>
        </tbody>
    </table>
 </div>
</body>
</html>
```
