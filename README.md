# Spring sts -Project - mini Homepage
스프링 STS + JSP 싸이월드 미니홈피

## 프로젝트 소개 🖥️
싸이월드 메인 홈페이지와 미니홈피를 참고하여 만든 사이트 입니다.

## 개발 기간 ⏱️
24.05.07 - 24.05.13

### 맴버 구성 🧑‍🤝‍🧑
- 김종민:
- 박서경:
- 오승민:
- 한다솔: 다이어리 파트 담당(프론트앤드, 백앤드)

### 개발 환경 ⚙️
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![jQuery](https://img.shields.io/badge/jquery-%230769AD.svg?style=for-the-badge&logo=jquery&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)

## 주요 기능 📌
- DB값 겅증
- 로그인, ID찾기, PW찾기
- 로그인시 세션 생성

# 주요 코드
### JAVASCRIPT
    $(document).ready(function() {
    // 리스트 선언
    let reply_list = [];
    
    <c:forEach var="blist" items="${reply}" varStatus="status">
    // 서버에서 받은 LIST 구조형 자료를 자바스크립트 변수에 저장
    reply_list.push({num:"${blist.dr_num}",// 작성된 다이어리 순번
    writer:"${blist.dr_writer}", // 다이어리 작성자
    content:"${blist.dr_content}",// 다이어리 내용
    code:"${blist.dr_code}"});// 유저 코드    
    </c:forEach>
    
    reply_list.forEach(function(arr) {
    // 위 자바스크립트에 저장된 변수를 활용하여 댓글 끌어오기
    const list = $(`#cmtlist\${arr['num']`);
    const plus = `<p>\${arr['writer']} : \${arr['content']} </p> <hr>`;
    list.append(plus); 
    });
    
### 추후 아래 코드를 적용할 예정
전반적인 코드 설명: 새로고침 없이 댓글 남기기, 삭제 등 구현

@Controller -> @RestController 사용

### JAVASCRIPT

    function deldir(code){ 
    // 다이어리 삭제
    $("#diary" + code).attr("style", "display: none;"); // 삭제시 화면에서 지움
    // ajax를 이용하여 서버로 삭제할 다이어리 코드 전달
    }

    const writecmt = (num) => { // 댓글 작성
    let a = $(`#comt\${num}`);
    const list = $(`#cmtlist\${num}`);
    const plus = `<p>익명인 : \${a.val()} </p>`;
    a.val('');
    list.append(plus);
    // ajax를 이용하여 서버로 추가된 댓글과 다이어리 코드 전달
    }
