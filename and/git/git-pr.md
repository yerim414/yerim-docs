# Git PR

사용하고 있던 기존 저장소에서 Git Lab으로 저장소를 이관하면서 PR을 도입하자 하였다.

PR이란 **Pull Request**, 한 브랜치에서 작업한 내용을 **다른 브랜치에 Merge 해 달라고 요청하는 것이다.**



기본 흐름은 다음과 같다

```
main
 │
 └── feature 브랜치
       │
       ├── 코드 수정
       ├── commit
       └── push
             │
             ▼
            PR
             │
          코드 리뷰
             │
             ▼
           Merge
             │
             ▼
            main
```

**작업 → commit → push → PR → Review → Merge**

Main 브랜치에서 Feature 브랜치를 뻗어 나간 뒤 다시 Main으로 Merge하는 흐름이다.

내가 작업한 내용을 Main에 반영 할 수 있도록 요청을 만드는 것이다.

참고로 Git hub 에서는MR(Merge Request)라고 한다. 명칭만 다르지 기능은 같다.
