# writing-well

William Zinsser 『On Writing Well』의 방법으로 산문을 쓰고 고치는 Claude Code 스킬 + 서브에이전트.

> A Claude Code skill and subagent that drafts and revises prose using William Zinsser's method. The rules are written in Korean; the principles aren't.

---

## 고치기 전과 후

### 1. 필자 머릿속에만 있던 고리

한로로 「나침반」 감상문 초고. 인용한 가사는 이렇다.

> 한 걸음, 두 마음, 세상이 내다 버린 우린

| | |
|---|---|
| **before** | 하나,둘,셋,넷이 음절 안에 있다. |
| **after** | **한·두·세·내.** 하나 둘 셋 넷이 음절 안에 있다. |

글에서 제일 센 발견인데, 어느 음절인지 짚지 않으면 처음 읽는 사람은 찾지 못한다. 문장이 틀린 게 아니라 고리가 빠진 것이다. 맞춤법 검사기는 이걸 못 잡는다. "더 매끄럽게 고쳐줘"도 못 잡는다.

같은 통과에서 인용 오차 네 건이 함께 나왔다 — `썬명히`→`선명히`, `결국에`→`결국엔`. 인용부호 안이 한 글자 틀리면 그 뒤의 주장까지 의심받는다.

### 2. 사람도 동사도 없는 문장

| | |
|---|---|
| **before** | 리스크 관리 설계의 중요성이 핵심 교훈이었다. |
| **after** | 나는 규칙보다 먼저 최악의 날을 계산해야 했다. |

주어가 중요성·필요성·활용·개선 같은 개념명사면 뒤집는다. 완충어(좀·다소·사실상)와 가치 선언어(놀랍게도·물론)는 지운다. **약간 대담하지 마라. 대담하라.**

### 3. 없는 숫자를 만들지 않는다

재료를 주지 않으면 모델은 지어낸다. 지어낸 문장이 제일 잘 읽히기 때문이다.

**before**

```
응답 시간이 340ms에서 90ms로 줄었다. 동료가 말했다. "이제야 쓸 만하네."
```

**after**

```
응답 시간이 [before ms]에서 [after ms]로 줄었다.

## 채워야 할 것
- [ ] 실제 측정치와 측정 조건
- [ ] 누가 뭐라고 했는지 (있었다면)
```

글의 모양은 완성하되 구체가 들어갈 자리는 비워 표시한다. "검증 가능한 구체 3개 이상"이라는 자기 요구를 채우려고 숫자를 지어내면 구체 세 개를 얻고 글 전체를 잃는다. 없던 대화를 인용으로 만드는 순간 그 글은 실패다.

이 규칙이 저장소의 다른 모든 규칙 위에 있다.

## 설치

```
/plugin marketplace add OkminLee/writing-well
/plugin install writing-well
```

<details>
<summary>플러그인 없이 파일로 넣기</summary>

```bash
git clone https://github.com/OkminLee/writing-well.git
cp -r writing-well/skills/writing-well ~/.claude/skills/
cp writing-well/agents/writing-well.md ~/.claude/agents/
```

</details>

## 쓰는 법

**스킬** — 글을 쓰거나 고칠 때 알아서 걸린다. 직접 부르려면 `/writing-well`.

**에이전트** — 글 자체가 산출물일 때 위임한다. 요청 문구로 모드가 갈린다.

| 요청 | 모드 | 산출물 |
|---|---|---|
| "~에 대해 써줘" | `WRITE` | 완성된 글 |
| "이 글 고쳐줘" | `REVISE` | 고친 글 + 무엇을 왜 바꿨나 + 손대지 않은 것 |
| "구조 먼저 잡아줘" | `STRUCTURE` | 6개 결정 + 뼈대 + 리드·엔딩 후보 (본문은 안 씀) |

어느 모드로 가든 순서는 고정이다. **재료 게이트** → **쓰기 전 6개 결정**(축소·요점·자격·톤·리드 재료·엔딩 재료) → **리드·본문·엔딩** → **3회 통과**(의미·가지치기·소리). 가지치기에서 초고가 30~50% 줄지 않았으면 통과를 안 한 것이다.

## 라이선스

문서는 MIT. 방법론의 출처인 William Zinsser, *On Writing Well*, 6th ed. (HarperCollins, 2001)의 저작권은 저자와 출판사에 있고, 여기 담긴 것은 그 원칙을 적용하려고 새로 쓴 운영 규칙이다.

더 깊이 가려면 책을 읽어라.

> 버릴 수 있는 모든 것에 감사하라.
