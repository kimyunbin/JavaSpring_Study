# Spring Boot Study

> [인프런 스프링 입문](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%9E%85%EB%AC%B8-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8) 을 들으며 공부한 내용들을 정리합니다.
>
> **초급자**를 위해 준비한 **[프레임워크 및 라이브러리, 웹 개발] 강의입니다.**
>
> 스프링 입문자가 예제를 만들어가면서 스프링 웹 애플리케이션 개발 전반을 빠르게 학습할 수 있습니다.



## ❗❗ 스터디 진행 과정 및 Github Push 방법❗❗

1. 본인 branch로 이동한 뒤, master에 있는 최신 파일 PULL 받아오기

   ```
   $ git switch 본인branch이름
   ```

   ```
   $ git pull origin master
   ```

2. 각 섹션별 해당 폴더에 들어가서

   `본인이름.md`

   파일을 추가한 뒤, 본인 branch에서 커밋 메세지 잘 지켜 푸쉬하기

   ```
   $ git add .
   $ git commit -m '커밋 메세지'
   $ git push origin 본인branch이름
   ```
   
3. 레포로 다시 돌아와서 Pull requests 탭 들어온 다음에 create pull request 

   master 브랜치와 Merge 

4. 스터디 끝나고 Merge가 완료된 후 branch 삭제하기

   > 관리자가 원격에 있는 브랜치는 삭제한 상태이므로 로컬 branch만 삭제해주기

   ```
   $ git switch master
   
   (master)
   $ git pull origin master  
   $ git branch -d 본인 branch 이름
   ```




---

<br>

## 목차 

- [**섹션 0. 강의 소개**](Section0)
- [**섹션 1. 프로젝트 환경설정**](Section1)
- [**섹션 2. 스프링 웹 개발 기초**](Section2)
- [**섹션 3. 회원 관리 예제 - 백엔드 개발**](Section3)
- [**섹션 4. 스프링 빈과 의존관계**](Section4)
- [**섹션 5. 회원 관리 예제 - 웹 MVC 개발**](Section5)
- [**섹션 6. 스프링 DB 접근 기술**](Section6)
- [**섹션 7. AOP**](Section7)
- [**섹션 8. 다음으로**](Section8)



