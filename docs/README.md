# 2주차 미션 - 자동차 경주     


[] indent의 depth가 3을 넘지 않게 작성하기.   
[] 기능목록마다의 테스트를 진행하기.    
[] 깃 커밋 메세지 의미있게 작성하기.      
[] .gitignore 이용해보기.      
[] 변수와 함수명 의미있게 작성하기.      
[] eslint와 prettier 사용하기.   
[] EOL(end of line) 설정 확인하기.      


<br>
<br>

### 유의할 점    

  - 이번 미션은 1주차에 더해서, `함수를 분리`하고 `함수별로 테스트`를 작성하는 것이 목표.

  - 특히 기능을 구현하기 전에 기능 목록을 만들고, 기능 단위로 커밋 하는 방식으로 진행한다.   
    (커밋 컨벤션에 유의하며, 키워드를 잘 사용하자.)   
  - 코드 작성 시 추가된 유의사항들이 있다.
    (한 메서드의 indent의 depth가 3을 넘지 않도록 한다. ---> 2까지만 허용)   

  - `Jest`를 이용해서 내가 만든 기능목록의 테스트를 진행한다.   

  - 이밖에도, `깃 커밋 메세지 의미있게`, `.gitignore 이용하기`, `변수 또는 함수명 확실히 의도를 드러내기.`   
    `eslint와 prettier 사용하기`, `EOL(end of line) 설정 확인하기` 등의 유의사항이 있다.   


<br>

---   

<br>

### EOL 설정 변경    
 

- vscode 내의 설정에서 prettier을 이용해서 변경했다.
  운영체제에도 상관없이 알아서 `EOL`을 설정하도록 `auto`로 지정.   

- 운영체제마다 개행하는 방법(?)이 다르다.     

```   
윈도우 : CRLF(\r\n)
유닉스 : LF(\n)
맥OS : LF(\n)
```     

*CR*
```
가나다라마바사아자차카타파하 //여기서 엔터
(커서가 줄 맨 앞에 위치)
```

*LF*
```
가나다라마바사아자차카타파하 //여기서 엔터
                     (엔터 친 곳에 커서가 위치)   
```     

<br>
 

- 운영체제마다 EOL방법이 다르기에, git에서 문제가 생길 수 있다.   
  이를 방지하고자 `autocrlf` 설정을 해야한다.    




- Windows   
  윈도우에서는 아래처럼 autocrlf를 true로 설정하여 위와 같은 효과를 기대한다.   
  >git config --global core.autocrlf true   


- Linux, Mac OS   
  리눅스, 맥, 유닉스는 LF 만 사용하므로 autocrlf 값을 input 으로 설정하여 Commit할 때만 (혹시나 있을 수도 있는) CRLF를 LF로 변환하도록 설정한다.   
  >git config --global core.autocrlf input


<br> 

---   

<br>


### eslint & prettier 설정    

- `eslint`는 `Linter`이고, 이는 소스코드에 문제가 있는지 검사하는 소프트웨어 도구이다.   

- `prettier`는 `Formatter`이고, 소스코드를 일관되게 작성하게끔 코드를 변환해주는 소프트웨어 도구이다.   

<br>

- `eslint`의 설치는 간단하다.   
  `npm init @eslint/config` 이후 상황에 맞게 선택지를 고르면 된다.   

- `prettier`의 설치는  
  `npm i -D prettier eslint-config-prettier` 이후에, 루트폴더에 `.prettierrc`를 추가한다.   
  이후에 해당파일에 자신의 컨벤션을 작성한다.   

  ```
  {
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "useTabs": false,
  "printWidth": 80,
  "bracketSpacing": true,
  "arrowParens": "always",
  "endOfLine": "auto"
  }
  ```   

  또한 `eslint`와 `prettier`의 충돌을 방지하기위해 `eslint-config-prettier`를 설치하고,
  `.eslintrc.cjs` 파일의 extends에 `prettier`을 추가한다.   

  > extends: ['airbnb-base', 'prettier']   

<br>

- vscode에서의 eslint & prettier 설정   

  vscode의 extensions 탭에서 eslint 와 prettier을 설치한다.   
  그리고 settings.json에 밑의 내용을 추가한다.   

  ```
  // 파일을 저장할 때마다 `eslint` 규칙에 따라 자동으로 코드를 수정
  "editor.codeActionsOnSave": { "source.fixAll.eslint": true },

  // `prettier`를 기본 포맷터로 지정
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  // 파일을 저장할 때마다 포매팅 실행
  "editor.formatOnSave": true
  ```     

<br>

- 또한 미션의 제한사항을 eslint로 설정해서 편리하게 관리한다.(.eslintrc.cjs 에 작성)

  (들여쓰기 2까지만 허용)
  ```
  rules: {
    // 들여쓰기 깊이 제한
    'max-depth': ['error', 2],
  },
  ```