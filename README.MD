# 잡초농가 팀 ToDoList 프로젝트

- Preview
![프리뷰 이미지](./resource/preview-2.png)

todolist를 localStorage 라이브러리를 이용해서 관리하는 프로젝트입니다.

<br>

---

# 📋  핵심 기능 요약
| 구분              | 기능 설명                                      | 관련 함수 및 설명                                                    |
| -------------- | ------------------------------------------ | --------------------------------------------------------- |
| 📝 할 일 추가   | 입력 후 버튼 클릭 또는 Enter 키로 할 일 추가              | `handleAdd`, `createItemObject`, `addItemArray`, `renderItem` |
| 🗑 할 일 삭제    | 리스트의 휴지통 아이콘 클릭 시 해당 항목 삭제                 | `handleRemove`, `removeItemArray`, `removeItem`               |
| ✅ 완료 처리    | 체크 아이콘 클릭 시 완료 여부 전환                       | `handleComplete`, `getCompleteTodoListArray`, `removeItem`    |
| 📂 탭 전환     | 완료/미완료 탭 클릭 시 해당 리스트 필터링                   | `moveToCompleteTab`, `moveToInCompleteTab`, `renderTab`       |
| 📦 로컬 저장   | 추가/삭제/완료 시 `localStorage`에 자동 저장           | `getStorage`, `setStorage`                                    |
| 🔄 초기 렌더    | 페이지 로드시 저장된 목록 불러와 렌더링                     | `init`, `renderItem`                                          |
| 🕒 날짜 표시    | 항목 추가 시 등록일을 표시, 1\~3일 이내/오래된 항목은 색상 차등 표시 | `dateFormat`, `getDateDiff`, `fontColorClasses`               |
| 🎨 색상 분류    | 날짜 기준으로 글자색 스타일 지정 (오늘/근접/오래됨)             | `getDateDiff`, `fontColorClasses`                             |
| 🎯 접근 방식    | 각 `<li>` 항목에 `data-id` 부여하여 식별 및 DOM 조작    | `createItem`, `removeItem`, 이벤트 위임 방식                         |


<br>

---

# 🛠️ 사용 기술 스택

| 분류    | 기술                                                 |
| ----- | -------------------------------------------------- |
| 언어    | `HTML`, `CSS`, `JavaScript`                        |
| 저장 방식 | `localStorage`                                     |
| 환경    | `Vanilla JS` 기반 모듈화 (`import/export`) |
| 스타일   | CSS 모듈 방식, 애니메이션 및 상태 변화 클래스 적용                    |
| 기타    | `VS Code`, `Prettier` 코드 포맷 설정                     |

<br>

---


<br>

# 기능 구현 상황

- 프로젝트 디자인
    - figma 이용해 node들의 사이즈 정의함.
- HTML, CSS 구현
    - 반응형으로 동작하도록 대부분의 오브젝트 사이즈를 vw, vh로 정의함.
    - 인터렉션 기능들 추가로 구현 완료
- 클릭 이벤트, `submit` 이벤트 등 관리
- TODO  `localStorage` 저장, 삭제
- TODO 노드요소 삽입 구현
- TODO 완료, 미완료 상태 구현
- 완료, 미완료 탭 이동 구현
- 등록 날짜 기준 하이라이팅 구현

---

<br>

# Ver 1.0a

lib 디렉터리 유틸 함수 구현 및 디렉터리 구조 설계

![alt text](./resource/filelist.png)

``` javascript
export function getNode(separator){
    return document.querySelector(separator);
}

export function insertLast(parent, htmlString){
    parent.insertAdjucentHTML("beforeend", htmlString);
}
```

<br>

---

# Ver 1.01a
node id, class 정의

\* css 디자인 중에 추가된 부분 (사전 정의 이후)

``` html
      <!-- 입력란 section -->
      <section class="add-todo-section">
        <!-- 폼 관련 내용 추가 -->
        <form id="add-todo-form">
          <button type="button" id="add-todo-btn">+</button>
          <input
            id="add-todo-input"
            type="text"
            placeholder="오늘 할 일 추가하기. 엔터키를 눌러 추가할 수 있습니다."
          />
        </form>
      </section>
```
시맨틱 구조 강화를 위해 폼 관련 내용이 추가되었습니다.

<br>

``` html
      <!-- todo 리스트 main -->
      <main>
        <ul id="todo-list-ul">
          <!-- 1번 li -->
          <li class="todo-list-cell">
            <div class="align-wrap">
                ...
            </div>
            <div class="align-wrap">
                ...
            </div>
        </li>
```
레이아웃 배치를 위해 align-wrap으로 각각 todo-list-complete-btn와 todo-list-text, todo-list-date 와 todo-list-optional 을 묶었습니다.

<br>

``` javascript
let inputForm = document.querySelector('#add-todo-form')

// form submit 처리 방지
inputForm.addEventListener('submit', (e) => { 
    e.preventDefault();
})

```
input 영역에 form이 추가됨으로써, submit action 방지를 위해 index.js에 추가되었습니다.

현 Preview에 보이는 내용으로 화면 구현 완료하였습니다. 버튼을 제외한 모든 요소가 vw, vh로 설계되어 반응형으로 작동합니다.

<br>

---
# Ver 1.1b

기존에 정의된 요구사항 모두 구현 완료
- TODO 추가
- TODO 삭제
- TODO 완료처리
- TODO 날짜 기반 하이라이팅
- TODO 완료, 미완료 탭 이동

팀원들 코드별로 merge 완료했습니다. 주석으로 작성자의 이름이 적혀 있습니다.

