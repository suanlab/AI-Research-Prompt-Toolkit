# Top-Tier Conference Paper Style Guide

NeurIPS/ICML/ICLR 급 논문 작성을 위한 통합 스타일 가이드.
6편의 NeurIPS accept 논문 분석 + 일반적인 best practice 종합.

---

# Part I. 논문 구조와 문장 스타일

---

## 1. Title

### 1.1 패턴

| 패턴 | 예시 |
|------|------|
| **[모델명] + [핵심 기여]** | Memory Mosaics at Scale |
| **[일반화된 개념] + for [대상]** | Generalized Linear Mode Connectivity for Transformers |
| **[시스템명]: [설명적 부제]** | JailbreakBench: An Open Robustness Benchmark for Jailbreaking LLMs |
| **[개념명]: [도발적 부제]** | Nested Learning: The Illusion of Deep Learning Architectures |
| **[주장문]** | Breaking the Performance Ceiling in RL requires Inference Strategies |

### 1.2 원칙

- 5~15단어. 짧을수록 기억에 남는다.
- 고유명사(모델/시스템명)는 앞부분에 배치.
- 부제 사용 시 콜론(:)으로 구분.
- 약어(LLM, RL 등)는 해당 커뮤니티에서 보편적일 때만 사용.
- 제목만 읽어도 "무엇을 했는가"가 드러나야 한다.

---

## 2. Abstract (150~250 단어)

### 2.1 흐름 템플릿

```
[배경/동기 1~2문장]
→ [기존 한계/gap 1~2문장] (However / Despite ...)
→ [본 논문의 제안 1~2문장] ("In this work, we ...")
→ [방법 요약 2~3문장]
→ [핵심 결과 2~3문장] (구체적 수치 포함)
```

### 2.2 좋은 Abstract의 조건

- **자기 완결적**: Abstract만 읽어도 논문 전체를 파악할 수 있어야 한다.
- **수치 포함**: 최소 1개의 구체적 정량 결과 ("outperforms by 10%", "up to 126% improvement").
- **이탤릭**: 핵심 개념 첫 등장 시 (*in-context learning*, *linear mode connectivity*).
- **Bold**: 극히 제한적으로 사용 (핵심 수치 1곳 정도).
- 기여를 "(1) ... (2) ... (3) ..." 형태로 나열해도 좋다.
- "In this paper/work, we" 로 전환 — 리뷰어가 기여를 즉시 식별.

### 2.3 실전 예시

> [배경] Memory Mosaics, networks of associative memories, have demonstrated appealing in-context learning capabilities on medium-scale networks and synthetic datasets. [한계] This work shows that these favorable properties remain when we scale to large model sizes and real-world datasets. [제안] To this end, we scale memory mosaics to 10B size, train them on one trillion tokens, and introduce architectural modifications ("memory mosaics v2"). [결과] A memory mosaics v2 trained on one trillion tokens still performs better than a transformer trained on eight trillion tokens.

---

## 3. Introduction

### 3.1 흐름 템플릿

```
[광범위 맥락/동기 1~2단락]
→ [구체적 문제/한계 1~2단락] ("However, ..." / "Despite ...")
→ [본 논문의 접근 1단락] ("In this work, ..." / "To this end, ...")
→ [기여 목록 1단락] (3~5개 항목)
→ [논문 구성 안내 (선택)] ("The rest of the paper is organized as follows...")
```

### 3.2 첫 문장 패턴

| 유형 | 예시 |
|------|------|
| Grand opening | "Understanding the geometry of neural network loss landscapes is central to both theoretical and practical advances in deep learning." |
| 최근 동향 | "Large language models (LLMs) are often trained to align with human values, thereby refusing to generate harmful or toxic content." |
| 역사적 맥락 | "For decades, AI research has focused on designing machine learning algorithms that learn from data or experience." |

**원칙**: 첫 문장은 해당 분야의 누구나 동의할 수 있는 광범위 진술. 너무 좁으면 독자를 잃고, 너무 넓으면 공허하다.

### 3.3 전환 문장 (Gap → Our approach)

**한계 지적:**
> However, we still lack a clear understanding of how current transformers achieve these capabilities.

**질문 제기:**
> Therefore, we ask *"How can we scale memory mosaics to large networks and real-world datasets?"*

**동기 연결:**
> This observation motivates us to ...  /  To address these challenges, we introduce ...

### 3.4 기여(Contribution) 목록 — 권장 패턴

**가장 효과적: Bold 키워드 + 설명 + (Section 참조)**

> This paper advances the understanding through the following key contributions:
>
> i **Unified symmetry framework:** We formalize a broad class of parameter transformations — including permutations, semi-permutations, orthogonal transformations, and general invertible maps (Section 3).
>
> ii **LMC for Transformers:** We demonstrate, for the first time, low- and zero-loss linear paths between independently trained Vision Transformers and GPT-2 models (Section 4 and 5).

**원칙:**
- 3~5개 기여 항목.
- Bold 키워드로 리뷰어가 스캔 가능하게.
- 각 기여에 Section 번호 참조 포함.
- "for the first time", "novel", "state-of-the-art" 등은 사실일 때만 사용.

### 3.5 잘 쓰인 Introduction의 체크리스트

- [ ] 첫 문장이 분야 전체를 아우르는가?
- [ ] 기존 연구의 한계가 명확히 서술되었는가?
- [ ] "Why now?" — 이 논문이 지금 필요한 이유가 드러나는가?
- [ ] 기여 목록이 구체적이고 검증 가능한가? (vague claim 금지)
- [ ] 각 기여가 실험/이론으로 뒷받침되는 Section과 연결되는가?
- [ ] Introduction만 읽어도 논문의 전체 그림이 그려지는가?

---

## 4. Related Work / Background

### 4.1 구조 선택

| 배치 | 적합한 경우 |
|------|-----------|
| Introduction 직후 (Section 2) | Background 지식이 Method 이해에 필수적일 때 |
| Conclusion 직전 (후반부) | 실험 결과를 본 후 비교가 더 의미 있을 때 |
| Background + Related Work 분리 | Background(수학적 토대)와 Related Work(선행 연구 비교)가 성격이 다를 때 |
| 통합 | 짧은 논문, 벤치마크/시스템 논문 |

### 4.2 소제목(Bold inline heading) 사용

토픽별로 Bold inline heading으로 구분하면 가독성이 높다:

> **Linear Mode Connectivity (LMC).** LMC describes the existence of low-loss linear paths between independently trained networks. Early work on mode connectivity [Garipov et al., 2018] identified ...
>
> **Model merging and symmetry alignment.** Several approaches have exploited the symmetry structure of neural networks to enable one-shot model merging. ...

### 4.3 문장 패턴

**선행 연구 인용 → 한계 → 차별화** 3단 구성:

> Several state-of-the-art approaches leverage discrete neuron permutations [Singh and Jaggi, 2020, Ainsworth et al., 2022]. *[인용]*
> Although foundational, permutation symmetries alone do not capture the full range of symmetries exhibited by modern architectures. *[한계]*
> In contrast, our framework broadens the set of valid reparameterizations... *[차별화]*

### 4.4 인용 스타일

- **괄호형**: (Author et al., Year) — 문장의 일부가 아닐 때.
- **서술형**: Author et al. [Year] — 주어/목적어로 사용할 때.
- 한 문장 내 3~5개 인용 동시 등장은 보편적.
- 숫자형 [1–5] vs. 저자-연도형: 학회 템플릿에 따름.

### 4.5 잘 쓰인 Related Work의 체크리스트

- [ ] 가장 관련 높은 선행 연구 5~10편이 충분히 논의되었는가?
- [ ] 각 연구 그룹에 대해 "무엇을 했고 → 어떤 한계가 있는지" 명시했는가?
- [ ] 우리 방법과의 차이가 명확히 서술되었는가?
- [ ] 최신 연구(최근 1~2년)가 빠짐없이 포함되었는가?
- [ ] 인용이 공정한가? (경쟁 연구를 의도적으로 누락하지 않았는가?)
- [ ] Related Work가 지나치게 길지 않은가? (본문의 15% 이내)

---

## 5. Method

### 5.1 구조

```
[전체 개요/직관 1단락]
→ [Sub-section: 컴포넌트 A]
→ [Sub-section: 컴포넌트 B]
→ [Sub-section: 컴포넌트 C]
→ [전체 알고리즘 정리 (Algorithm 환경)]
```

### 5.2 수식 작성 원칙

**수식 전: 동기/직관 → 수식 후: 해석**

> Inspired by the asymptotic MISE kernel bandwidth estimation where 1/√β ∝ n^{-1/(p+4)}, memory mosaics v2 schedule β as:
>
> β = β₁ n^α + β₀ , (6)
>
> where β₀ ≥ 0, β₁ > 0, 1 > α > 0 are learnable parameters. I.e., the more key-value pairs, the smaller bandwidth.

**원칙:**
- 모든 수식에 번호를 매기고, 본문에서 "Equation (6)" 또는 "Eq. (6)"으로 참조.
- 수식 직후 반드시 "where ..." 로 변수 정의.
- 수식만으로 의미가 전달되지 않으면 직관적 해석을 1문장 추가.
- Notation은 논문 전체에서 일관되게 유지 (Notation 표 권장).

### 5.3 Bold inline heading

소제목(\subsection) 없이 단락을 구분할 때 사용:

> **Short-term memory.** The short-term memory at position t only stores key-value pairs of near-tokens, ranging from t − h + 1 to t − 1.
>
> **Long-term memory.** In contrast, the long-term memory skips near tokens and only stores key-value pairs before position t − m.

### 5.4 잘 쓰인 Method의 체크리스트

- [ ] 전체 파이프라인/아키텍처를 한눈에 보여주는 overview figure가 있는가?
- [ ] 각 컴포넌트의 설계 동기(why)가 설명되었는가?
- [ ] 모든 수식의 변수가 정의되었는가?
- [ ] 알고리즘이 재현 가능한 수준으로 서술되었는가?
- [ ] Notation이 논문 전체에서 일관적인가?
- [ ] 불필요한 수식 없이 핵심만 본문에, 나머지는 Appendix에 배치했는가?

---

## 6. Experiments / Results

### 6.1 구조

```
[실험 설정 개요]
  - 데이터셋, 모델 크기, 학습 하이퍼파라미터
  - Baseline 목록 + 선정 근거
  - 평가 메트릭 정의
→ [평가 차원 A: Sub-section]
  - Task description
  - Main results (Table/Figure 참조)
  - 분석/해석
→ [평가 차원 B: Sub-section]
→ [Ablation study]
→ [Analysis / Discussion]
```

### 6.2 결과 서술 패턴

**Table/Figure 참조 → 핵심 관찰:**
> Table 1 evaluates both memory mosaics v2 and baseline transformers on 19 commonly used language benchmarks, showing that they perform closely on these benchmarks.

**"We observe" 관찰형:**
> We can observe two phenomena: **1)** memory mosaics v2 consistently improve classification performance as it sees more demonstration shots (blue curves). **2)** Memory mosaics v2 significantly outperform transformers by more than 10%.

**수치 비교 직접 서술:**
> Memory mosaics v2 outperforms transformers on 4k task-length by 1.4%~5.6%.
> The resulting transformer (trained on 8T tokens) still lags behind memory mosaics v2 (trained on 1T tokens) by 6.5% (46.9% vs 53.4%).

**대비/반전:**
> In contrast, transformers struggle to maintain their performance.
> Surprisingly, a single fine-tuning mini-batch yields a 22% accuracy improvement.
> Interestingly, removing long-term memory achieves comparable performance while using fewer parameters.

### 6.3 비교 표현 사전

| 상황 | 표현 |
|------|------|
| 제안 > baseline | "outperforms ... by X%", "achieves X% improvement over" |
| baseline > 제안 | "lags behind ... by X%", "falls short of ... by X%" |
| 동등 | "performs comparably to", "on par with" |
| 압도적 차이 | "significantly outperforms", "by a large margin" |
| 예상 외 결과 | "Surprisingly, ...", "Counterintuitively, ..." |
| 괄호 내 수치 | "(46.9% vs 53.4%)", "(+10.3%)" |

### 6.4 잘 쓰인 Experiments의 체크리스트

- [ ] 실험 설정이 재현 가능한 수준으로 서술되었는가?
- [ ] Baseline이 공정하게 선정되었는가? (최신 SOTA 포함)
- [ ] 동일 조건(데이터, 파라미터 수, compute)에서 비교하고 있는가?
- [ ] 오차 막대(error bar) 또는 표준편차가 보고되었는가?
- [ ] Table/Figure의 핵심 수치가 본문에서도 언급되는가?
- [ ] Ablation study로 각 컴포넌트의 기여가 검증되었는가?
- [ ] 실패 사례/한계가 솔직하게 보고되었는가?

---

## 7. Discussion / Conclusion

### 7.1 구조

```
[핵심 기여 요약 1~2문장]
→ [주요 결과 재확인 2~3문장]
→ [의의/임팩트 1~2문장]
→ [한계 1~2문장]
→ [미래 연구 방향 1~2문장]
```

### 7.2 첫 문장 패턴

> This work scales memory mosaics to llama-8B scale, demonstrating superior performance on new task learning, outperforming transformers by more than 10%.

> We introduced a unified framework for symmetry-aware model alignment that captures a broad class of transformations.

### 7.3 Limitations 표현

**별도 소제목:**
> **Limitations.** While we tried to make our benchmark as comprehensive as possible, we had to restrict the scope of what is allowed for attackers.

**자연스러운 언급:**
> The empirical results were based on a smaller version of GPT-2 due to resource constraints, indicating the need for evaluation on larger models.

**원칙:**
- Limitations을 명시하면 리뷰어의 신뢰를 얻는다.
- "한계를 인식하고 있다"는 것 자체가 기여.
- NeurIPS 체크리스트에서 Limitations 항목이 필수.

### 7.4 미래 연구

> One future direction is to reduce the computational cost for very long context lengths.
> Beyond the broader RL setting, we intend to investigate two main future research directions. First, ... Second, ...

---

## 8. 문장 수준 스타일

### 8.1 시제 규칙

| 섹션 | 시제 | 예시 |
|------|------|------|
| Abstract | 현재 / 현재완료 | "have demonstrated", "we introduce", "we show" |
| Introduction | 현재 (일반론) + 현재완료 (선행 연구) | "remains challenging", "has been continuously pursued" |
| Method | 현재 (정의/설명) | "implements", "stores", "retrieves" |
| Experiments | 현재 (결과 해석) + 과거 (실험 수행) | "Table 1 evaluates", "We trained", "shows that" |
| Conclusion | 과거 (수행 요약) + 현재 (의의) | "We introduced", "These results reveal" |

### 8.2 인칭

- **"We"** 가 압도적 표준. "I" 는 단독 저자 논문에서만.
- **수동태**: 설정/조건 서술 시 간헐적 ("Both models are trained on...").
- **"This paper/work"**: Intro/Conclusion 첫 문장에서 주어로 사용.

### 8.3 강조 장치

| 장치 | 용도 |
|------|------|
| **Bold** | 모델명 첫 등장, 핵심 기여, inline heading, 극히 중요한 수치 |
| *Italic* | 개념 정의 첫 등장, 강조 구절, 인용 질문 |
| SMALL CAPS | 시스템/벤치마크/데이터셋 고유명 |
| `monospace` | 코드, 토큰, 변수명 |

### 8.4 전환어

| 전환어 | 용도 | 사용 빈도 |
|--------|------|---------|
| However | 한계/반전 | 매우 높음 |
| In contrast | 대비 | 높음 |
| Moreover / Furthermore | 추가 | 높음 |
| Specifically / In particular | 구체화 | 높음 |
| Interestingly / Surprisingly | 예상 외 결과 | 중간 (남용 금지) |
| To this end | 동기→방법 연결 | 중간 |
| Note that / It is worth noting | 부연 | 중간 |

### 8.5 수사적 장치

**질문 제기** — 섹션 전환이나 동기 부여에 효과적:
> *"How much more data does the transformer recipe approach need to match the performance of memory mosaics v2?"*

**비유/은유** — 직관적 이해 촉진 (단, 과용 금지):
> Consider a poor goldfish with 7-second memory — how can it possibly learn a 90-minute movie?

### 8.6 문장 길이

| 섹션 | 평균 단어 수 |
|------|-----------|
| Abstract | 25~35 |
| Introduction | 20~30 |
| Method | 15~25 (수식 전후 짧게) |
| Experiments | 20~30 |
| Conclusion | 25~35 |

**원칙:** 한 문장에 하나의 아이디어. 40단어 이상이면 분리를 고려.

---

# Part II. Table 스타일

---

## 9. 테이블 구조

### 9.1 기본 LaTeX 패턴

```latex
\usepackage{booktabs}

\begin{table}[t]
\caption{[주제 1문장]. [부연/조건 0~2문장].}
\label{tab:example}
\centering
\small
\begin{tabular}{l cc | ccccc | c}
\toprule
         & \multicolumn{2}{c}{Group A} & \multicolumn{5}{c}{Benchmarks} & \\
\cmidrule(lr){2-3} \cmidrule(lr){4-8}
Model    & param & config & bench1 & bench2 & ... & avg \\
\midrule
baseline 1 & ... & ... & 45.8 & ... & ... & 50.2 \\
baseline 2 & ... & ... & 46.1 & ... & ... & 51.0 \\
\midrule
ours       & ... & ... & \textbf{48.3} & ... & ... & \textbf{53.4} \\
\bottomrule
\end{tabular}
\end{table}
```

### 9.2 핵심 규칙

1. **booktabs 필수** — 세로선(vertical rule) 절대 금지.
2. 수평선: `\toprule` / `\midrule` / `\bottomrule` 만 사용.
3. 그룹 구분: `\cmidrule(lr){a-b}` 로 열 범위 지정.
4. 캡션은 테이블 **상단**에 배치.
5. `\small` 또는 `\footnotesize` 로 폰트 축소.

### 9.3 헤더 구성

- **2-level 그룹 헤더**: 상단=대분류 (모델/데이터셋), 하단=세부 벤치마크.
- 열 제목: 소문자 또는 첫 글자만 대문자. 약어 사용 가능.
- 메트릭 방향: ↑ (높을수록 좋음) / ↓ (낮을수록 좋음) 화살표 표시.
- 정렬: 모델명=좌측정렬, 숫자=우측 또는 소수점 정렬.

### 9.4 최고값 강조 규칙

| 규칙 | 설명 |
|------|------|
| **열(column) 단위 bold** | 각 열에서 최고값(또는 메트릭 방향에 따라 최소값)을 `\textbf{}` |
| 방향 따라 bold | accuracy/score → 최대값, perplexity/loss → 최소값 |
| 동점 처리 | 동점이면 모두 bold |
| 2nd best (선택) | underline(`\underline{}`) 또는 순위 번호. 1st만 표시해도 충분 |
| avg 열 | bold 적용 |
| 그룹 내 비교 | 모델 스케일별로 그룹 분리 시 그룹 내에서만 bold |

### 9.5 행/열 순서

**행 순서:**
1. Baseline 먼저 → 제안 방법 마지막 (리뷰어가 마지막 행에서 bold를 기대).
2. 모델 크기순으로 그룹 분리 (midrule 구분).
3. 성능 약한 순 → 강한 순 (클라이맥스 구조).

**열 순서:**
```
[model | params | config] | [benchmark₁ | benchmark₂ | ...] | [avg]
```
- 좌측: 식별 정보 (모델명, 파라미터 수, 설정).
- 중앙: 개별 벤치마크 결과 (약어 사용).
- 우측 끝: avg / mean 집계 열.
- 조건 변화 열 (context length, shots 등)은 값이 증가하는 순서.

### 9.6 숫자 포맷

- 동일 테이블 내 **소수점 자릿수 통일** (필수).
- Accuracy/Score: 소수점 1~2자리 (45.8 또는 45.83).
- Perplexity: 소수점 2자리 (26.05).
- 백분율: % 기호 사용 시 정수 또는 1자리 (90.3%).
- 오차: ± 뒤에 본 값과 동일 자릿수 (0.34 ± 0.01).

### 9.7 특수 기호

| 기호 | 의미 |
|------|------|
| `*` | 특수 설정, 하이브리드 모델, 외부 데이터 사용 |
| `×` | 해당 없음 / 실패 |
| `—` / `–` | 데이터 미보고 |
| `↑` / `↓` | 메트릭 방향 |
| `±` | 표준편차 / 표준오차 |
| `†` / `‡` | 추가 각주 표시 |

### 9.8 캡션

```
Table N: [주제/내용 요약 1문장]. [부연 설명 또는 실험 조건 0~2문장].
```

- 캡션만 읽어도 테이블의 내용을 이해할 수 있어야 한다.
- Bold/색상 규칙이 비표준이면 캡션 끝에 명시 ("bold indicates best").
- 특수 기호(*)의 의미를 캡션 내에서 설명.
- 길이: 1~4문장 (10~80단어).

---

# Part III. Figure 스타일

---

## 10. Figure 레이아웃

### 10.1 유형별 권장 레이아웃

| Figure 유형 | 권장 레이아웃 |
|------------|-----------|
| Architecture / Pipeline | 수직 스택 (bottom-up flow), Left/Right 비교 |
| 실험 결과 비교 (동일 메트릭) | 2~3 panel 가로 배열 (task별 subplot) |
| 보조 결과 / 작은 분석 | 본문 우측 wrap (wrapfigure), 단일 panel |
| Heatmap / Contour 매트릭스 | row=method, col=task, 공유 colorbar 우측 |
| Ablation | 단일 panel bar chart 또는 line plot |

### 10.2 Sub-panel 레이블

- **(a)**, **(b)**, **(c)** — 가장 표준적.
- **Left:**, **Right:** — 캡션에서 직접 구분.
- 혼용하지 않는다. 한 논문 내에서 일관되게.

### 10.3 축/레이블 원칙

- X-Y 축 레이블 **항상** 포함.
- 축 제목: 첫 글자만 대문자 ("Accuracy", "Number of shots").
- Grid: 없거나 약한 grid (회색, 얇은 선).
- 폰트 크기: 축 레이블 8~10pt, 범례 7~9pt.
- 모든 축의 단위를 명시.

---

## 11. Figure 색상

### 11.1 색상 할당 원칙

| 역할 | 권장 색상 |
|------|---------|
| 제안 방법 (Ours) | **파랑** 또는 **초록** |
| Baseline / 기존 방법 | **빨강** 또는 **회색** |
| 2nd 제안 방법 | **주황** 또는 **보라** |
| 추가 비교 대상 | Matplotlib tab10 팔레트에서 선택 |

### 11.2 시각적 원칙

- **2~4색 팔레트**로 절제. 5색 이상은 범례가 복잡해진다.
- **실선(—) = 주요 모델**, **대시(--) = secondary/baseline**.
- 마커(o, *, △)로 모델/조건 추가 구분.
- **백색 배경**, border/frame 없음.
- 색맹 친화적 팔레트 권장 (파랑-주황, viridis 등).
- **벡터 그래픽(PDF)** 출력 기본 — 래스터(PNG)는 screenshot 등 특수한 경우만.

### 11.3 Colormap 선택

| 데이터 유형 | 권장 Colormap |
|-----------|-------------|
| Diverging (양/음 대비) | RdBu, coolwarm |
| Sequential (단방향) | viridis, plasma, inferno |
| Categorical | tab10, Set2 |

---

## 12. Figure 캡션

### 12.1 기본 구조

```
Figure N: [Bold 핵심 메시지 또는 제목]. [상세 설명 1~3문장].
```

### 12.2 효과적인 캡션 패턴

| 패턴 | 예시 | 적합한 경우 |
|------|------|-----------|
| Bold 핵심 문장 + 설명 | "**Improvement from using inference-time search.** Across 17 tasks, we obtain..." | 실험 결과 figure |
| Left/Right 구분 | "**Left:** Memory Unit. **Right:** Architecture." | 2-panel 비교 |
| (a)/(b) sub-caption | "(a) illustrates ..., and (b) shows ..." | multi-panel |
| 주장/결론 전달 | "Augmenting transformer with long-short term attention doesn't help." | 핵심 발견 강조 |

### 12.3 캡션 작성 원칙

- 캡션만 읽어도 figure의 메시지를 이해할 수 있어야 한다.
- 색상/선 스타일을 캡션에서 직접 참조: "(blue curves)", "(dash red line)".
- 구체적 수치 포함: "outperforms by 12.3%~14.8%".
- 다른 Figure/Table 참조 가능: "see Figure 1", "Numbers are copied from Table 4".
- 길이: 단순 diagram 1문장, 실험 결과 2~4문장.

---

# Part IV. 논문 전체 수준의 품질 원칙

---

## 13. Storytelling — 논문은 하나의 이야기

### 13.1 The One-Sentence Paper

모든 논문은 한 문장으로 요약 가능해야 한다:

> "Memory mosaics v2 demonstrates that scaling associative memory architectures to 10B parameters and 1T tokens achieves superior new-task learning ability that transformers cannot match even with 8× more data."

이 한 문장이 Title → Abstract → Introduction → Experiments → Conclusion 을 관통하는 **주선율(main thread)** 이다.

### 13.2 Reader-First 원칙

- **리뷰어는 바쁘다.** Abstract, Figure 1, Table 1, Conclusion만 읽는 리뷰어도 논문의 핵심을 파악할 수 있어야 한다.
- **Figure 1은 논문의 얼굴.** 전체 아이디어를 한 장으로 압축하는 overview figure 또는 가장 인상적인 결과.
- **각 섹션의 첫 문장이 그 섹션의 요약.** 첫 문장만 이어 읽어도 논문의 골격이 보여야 한다.

### 13.3 Claim과 Evidence의 균형

- 모든 claim은 실험/이론으로 뒷받침되어야 한다.
- "novel", "state-of-the-art", "for the first time" — 검증 가능한 경우에만 사용.
- 과장하지 않되, 자신의 기여를 축소하지도 않는다.

---

## 14. Clarity — 명확성

### 14.1 Notation 일관성

- Notation 표(Notation table)를 Appendix에 포함하거나, 각 기호를 첫 등장 시 정의.
- 동일 기호에 두 가지 의미를 부여하지 않는다.
- 벡터=bold 소문자(**x**), 행렬=bold 대문자(**W**), 스칼라=이탤릭(α), 집합=캘리그래피(D).

### 14.2 용어 일관성

- 같은 개념에 같은 용어를 사용. "short-term memory"와 "working memory"를 혼용하지 않는다.
- 약어는 첫 등장 시 풀어쓰고 ("Reinforcement Learning (RL)"), 이후 약어만 사용.

### 14.3 단락 구조

- 한 단락 = 하나의 아이디어.
- 단락 첫 문장이 topic sentence (단락 요약).
- 5~8문장이 적정. 10문장 이상이면 분리.

---

## 15. Reproducibility — 재현 가능성

### 15.1 실험 세부사항

다음을 반드시 보고 (본문 또는 Appendix):

- [ ] 모델 아키텍처 상세 (layer 수, hidden dim, head 수 등)
- [ ] 학습 하이퍼파라미터 (lr, batch size, optimizer, scheduler, epochs)
- [ ] 데이터셋 상세 (크기, 전처리, train/val/test split)
- [ ] 하드웨어 (GPU 종류, 수량)
- [ ] 학습 시간 / 총 compute
- [ ] Random seed 및 실행 횟수
- [ ] 코드 공개 여부

### 15.2 오차 보고

- 3회 이상 실행의 평균 ± 표준편차(또는 표준오차) 보고.
- 어떤 변동 요인(seed, data split 등)에 대한 오차인지 명시.
- 95% bootstrap confidence interval도 좋은 대안.

---

## 16. Ethics & Broader Impact

### 16.1 NeurIPS 체크리스트 (필수)

NeurIPS 2024/2025 기준 체크리스트 항목:
1. Claims — Abstract/Introduction이 기여를 정확히 반영하는가?
2. Limitations — 한계를 논의했는가?
3. Theory assumptions and proofs — 이론 결과의 가정과 증명이 완전한가?
4. Experimental result reproducibility — 재현 가능한가?
5. Open access to data and code
6. Experimental setting/details
7. Experiment statistical significance — 오차 막대를 보고했는가?
8. Experiments compute resources
9. Code of ethics
10. Broader impacts

### 16.2 Limitations 작성 원칙

- 솔직하게 쓴다 — 리뷰어는 은폐된 한계를 더 부정적으로 본다.
- 한계를 인식하되, 미래 연구 방향으로 자연스럽게 연결.
- "While our work focuses on X, extending to Y remains an important direction."

---

## 17. Appendix 활용

### 17.1 Appendix에 넣어야 할 것

- 본문에 넣으면 흐름이 깨지는 **세부 증명, 유도 과정**.
- **추가 실험 결과** (ablation, 추가 벤치마크, 추가 baseline).
- **학습/평가 세부사항** (하이퍼파라미터 표, 데이터 전처리, 프롬프트 예시).
- **Notation 표**.
- **추가 Figure/Table** (본문 공간 부족 시).

### 17.2 Appendix 참조 방식

- 본문에서 "(see Appendix A for details)", "(detailed in Appendix C)" 형태로 참조.
- Appendix가 있음을 리뷰어가 인지하도록 본문 곳곳에서 언급.

---

## 18. 최종 제출 전 체크리스트

### 18.1 내용

- [ ] Title이 논문 내용을 정확히 반영하는가?
- [ ] Abstract가 자기 완결적이며 구체적 수치를 포함하는가?
- [ ] Introduction의 기여 목록이 실험/이론과 1:1 대응하는가?
- [ ] 모든 claim이 evidence로 뒷받침되는가?
- [ ] 모든 수식의 변수가 정의되었는가?
- [ ] Related Work에서 주요 선행 연구를 빠짐없이 논의했는가?
- [ ] Limitations을 솔직하게 서술했는가?
- [ ] NeurIPS 체크리스트를 성실하게 작성했는가?

### 18.2 Table & Figure

- [ ] 모든 Figure/Table이 본문에서 참조되는가?
- [ ] 캡션만 읽어도 Figure/Table을 이해할 수 있는가?
- [ ] Table에서 세로선을 사용하지 않았는가? (booktabs)
- [ ] 최고값 bold가 일관되게 적용되었는가?
- [ ] Figure 색상이 색맹 친화적인가?
- [ ] 모든 축에 레이블과 단위가 있는가?
- [ ] Figure가 벡터 그래픽(PDF)으로 출력되었는가?

### 18.3 형식

- [ ] 페이지 제한을 준수했는가? (NeurIPS: 본문 9p + references + appendix)
- [ ] 참고문헌 포맷이 학회 템플릿에 맞는가?
- [ ] 익명성이 유지되었는가? (Blind review 시)
- [ ] 하이퍼링크가 파란색으로 적절히 보이는가?
- [ ] 오타/문법 검수를 완료했는가?
- [ ] PDF 파일 크기가 제한 이내인가?

---

## Quick Reference Card

```
┌─────────────────────────────────────────────────────────────┐
│  TITLE        5~15 words, 핵심이 즉시 드러나게                 │
│  ABSTRACT     배경→한계→제안→방법→결과(수치), 150~250 words    │
│  INTRO        Grand opening→Gap→Our approach→Contributions  │
│  METHOD       직관→수식→해석, overview figure 필수             │
│  EXPERIMENTS  설정→결과(Table/Fig 참조)→분석, ablation 포함    │
│  CONCLUSION   요약→의의→한계→미래, 과장 금지                   │
├─────────────────────────────────────────────────────────────┤
│  TABLE        booktabs, 세로선 금지, 열별 bold, baseline→ours │
│  FIGURE       2~4색, 제안=파랑, baseline=빨강, 벡터 PDF 출력  │
│  CAPTION      자기완결적, 색상/수치 직접 참조, 1~4문장          │
├─────────────────────────────────────────────────────────────┤
│  문장          We 주어, 한 문장=한 아이디어, 40단어 이하        │
│  강조          Bold=모델명/heading, Italic=개념 정의            │
│  수치          "(A% vs B%)", "outperforms by X%"              │
│  전환          However(반전), In contrast(대비), To this end   │
└─────────────────────────────────────────────────────────────┘
```
