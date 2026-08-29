# find-skills

클로드를 사용하고 나서는 그냥 유명한 스킬, 사람들이 많이 사용 하는 스킬위주로만 사용하였다.

물론 내가 직접 몇개 만들어 보았지만, 사람들이 많이 사용하는 스킬에는 이유가 있다.

클로드를 통해서 이것저것 다양한걸 부담없이 만들어 볼 수 있어 좋디만 그에 맞는 스킬을 찾기는 좀 불편했다.

그래서 좀 찾아보니 **스킬을 찾아주는 스킬**이 있다.

***

{% embed url="https://github.com/vercel-labs/skills/tree/HEAD/skills/find-skills" %}

이 스킬은 말그대로 내가 만들고자 하는 프로젝트에 대해 설명을 하면 그에 맞춰 외부 skill을 찾아주는 skill이다.

그런데 추천을 하지만 사람들이 잘 사용하지 않는 그런 스킬을 추천해주면 어떡하지..? 라는 생각을 했는데

```
### Step 4: Verify Quality Before Recommending

**Do not recommend a skill based solely on search results.** Always verify:

1. **Install count** — Prefer skills with 1K+ installs. Be cautious with anything under 100.
2. **Source reputation** — Official sources (`vercel-labs`, `anthropics`, `microsoft`) are more trustworthy than unknown authors.
3. **GitHub stars** — Check the source repository. A skill from a repo with <100 stars should be treated with skepticism.

```

이미 이 스킬에 검색 기준으로만 추천이 아닌, **설치횟수, 평판, Git hub 스타** 등 추천전에 그 스킬에 대해 검증하여 추천해준다.

꼭 신규 프로젝트가 아니여도 기존에 있던 프로젝트에서도 추천을 받아 사용하면 좋을 것 같다.

{% prompt description="이미 개발중인 프로젝트의 skill 추천" %}
```markdown
현재 프로젝트를 기준으로 개발에 도움이 될 만한 Skill을 찾아줘.

현재 프로젝트의 기술 스택, 테스트 방식, Docker 구성,
API 개발 방식 등을 먼저 파악하고,

1. 현재 프로젝트에 유용한 Skill
2. 각 Skill이 필요한 이유
3. 설치할Skill

을 구분해서 알려줘.

기존 프로젝트의 코드를 수정하거나 구조를 변경하지 말고
Skill 검색 및 추천만 수행해줘.
```
{% endprompt %}

한번 프롬프트도 작성해보았는데.

회사에서 작업중인 프로젝트에 해당 스킬을 이용해 봐야겠다
