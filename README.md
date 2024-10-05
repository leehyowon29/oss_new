# 제목 : LLaMA 3 에 대해 알아보자
---
## 팀원 :
+ 통계학과/2024009762/이효원 (leehyowon29)
+ 전자공학부 모바일공학전공/2024007587/홍은지 (zjseltus)
+ 통계학과/2024002789/이한선 (ihanseon)
+ 전자공학부 인공지능전공/2024003120/이가령 (GaRyeong9828)
---
# 1. Introduction
LLaMA 3는 Large Language Model Meta AI의 줄임말로 메타(구. 페이스북)에서 주도하는 오픈소스 언어모델이다.
2023년 2월 24일 LLaMA-1이 처음 공개 되었고, 이후 2023년 7월 18일에 LLaMA-2로 한번의 성능 향상을 이룬 뒤, 기업과 상용 모두에 공개하면서 관심을 끌기 시작한다.
2024년 4월 18일, 현재의 LLaMA-3가 공개되었고, 현재 meta.ai를 통해 영미권 국가들을 우선 대상으로 인스타그램 등 메타의 플랫폼에 챗봇으로 도입되었다.
이후 7월 23일, LLaMA-3.1 버전을 8B(Billion), 70B, 405B로 3가지 모델을 출시하면서, 8개 언어와 도구 사용을 지원하였다.
가장 규모가 큰 405B 버전은 GPT-4o, Claude 3.5 Sonnet과 견줄만한 성능을 갖춘 상태이다.

LLaMA는 엔비디아의 GPGPU 자원을 통한 인프라를 구축했으나, 엔비디아의 생산 차질로 인한 공급 이슈와 높은 가격, 비효율적인 전력 소모를 이유로 메타의 인공지능 가속기를 통한 개발 환경을 만들고 있다.
소프트웨어도 CUDA를 벗어나, 메타의 라이브러리인 PyTorch를 통해 컴파일러, 커널, 스트리밍API, 드라이버까지 독자 생태계 구축을 가속화시키고 있다.

1조 4000억개의 토큰으로 학습되었다.
해당 토큰은 페이스북, 인스타그램 등 메타의 패밀리앱 외에도 웹스크래핑/크롤링, 깃허브 코드, 위키피디아 텍스트, 퍼블릭 도메인 서적, LaTeX 코드로 작성된 논문, 질문질답 텍스트 등으로 학습되었다고 한다.

---
# 2. License

---
# 3. ...
- Llama 3.1의 문서요약기능이란?
 라마의 문서 요약기는 긴 문서를 더 짧고 소화하기 쉬운 버전으로 요약할 수 있는 기능입니다.

- Llama 3.1의 문서요약기능 작동방식
1. 텍스트 분석: 라마 모델은 전체 입력 텍스트를 분석하여 식별합니다
	- 주요 개념 및 실체
	- 중요한 이벤트 및 관계
	- 주요 논거 또는 주장
2. 문장 순위: 각 문장은 문서의 관련성, 중요성, 문서의 전반적인 의미에 대한 기여도를 기준으로 점수가 매겨집니다.
3. 요약문 생성: 요약문을 구성하기 위해 가장 높은 점수를 받은 문장을 선택합니다:
	- 간결한 버전(보통 원본 텍스트의 10~20%)
	- 일관된 내러티브 또는 핵심 사항
4. 후처리: 생성된 요약문은 다음과 같은 다양한 기술을 통해 개선됩니다
	- 문장 재작성 및 순서 변경
	- 중복 정보 제거

- Llama 3.1의 문서요약기능 작동원리
라마의 문서 요약 기능은 자연어 처리(NLP)를 사용하여 텍스트를 간소화합니다. 작동 원리를 요약하면 다음과 같습니다

1. 토큰화: 입력 텍스트는 토큰이라고 하는 개별 단어로 나뉩니다.
2. POS(Part-of-Speech) 태깅: 각 토큰은 문법적 맥락을 이해하기 위해 명사, 동사, 형용사, 부사 등으로 식별됩니다. POS 태깅이란 문장 내 단어들의 품사를 식별하여 태그를 붙여주는 것을 말합니다. 
3. 개체명 인식(Named Entity Recognition(NER)):  모델은 텍스트에서 사람, 조직, 위치 및 날짜와 같은 특정 객체를 식별합니다. 개체명 인식이란 텍스트문장에서 개체를 찾아서 미리 정의된 범주(사람 이름, 조직, 위치, 시간 , 날짜 등)으로 분류하는 자연어 처리(NLP) 방법입니다.
4. 의존 구문분석(Dependency Parsing): 주어-동사 관계와 같이 토큰이 어떻게 연관되는지 이해하기 위해 문장의 구조를 분석합니다. 의존 구문분석이란 문장보다는 문장에 존재하는 개별 단어 간 의존 또는 수식 방향으로 관계를 파악하여 문장 구조를 분석하는 방법입니다.
5. Semantic Role Labeling(SRL): 문장에서 개체의 역할을 식별하여 "누가 무엇을 했나요?"와 같은 질문에 답합니다. SRL이란 자동적으로 문장 내에 논항(argument)과 술어(또는 동사(verb))(predicate)를 분석하여 문장 내 성분에 시멘틱 롤 (semantic role)(또는 의미 역할, 의미역)을 부여하는 방법입니다.
6. 텍스트랭크 알고리즘(TextRank): 그래프 기반 알고리즘을 사용하여 텍스트 내의 연결을 기반으로 각 토큰과 문장의 중요도를 평가합니다. TextRank는 PageRank(하이퍼링크를 가지는 웹 페이지에 대해서 얼마나 참조가 됐는지, 또는 유입이 되었는지 등으로 페이지의 순위를 매기는 알고리즘)의 알고리즘을 활용한 것으로, 페이지의 개념을 단어의 개념으로 바꾼 알고리즘이다. 즉, 텍스트로 이루어진 글에서 특정 단어가 다른 문장과 얼마만큼의 관계를 맺고 있는지를 계산하는 것입니다.
7. 그래프 기반 요약(Graph-Based Summarization): 요약을 나타내는 연결된 하위 그래프를 형성하여 가장 중요한 문장과 토큰을 선택합니다.
라마 모델은 이 구조화된 정보를 사용하여 원본 문서의 핵심 사항, 주요 아이디어 및 지원 세부 정보를 식별합니다. 개체와 개념 간의 관계를 분석하여 콘텐츠의 본질을 포착하는 간결한 요약을 생성합니다.

라마는 이 구조화된 정보를 사용하여 원본 문서의 주요 아이디어와 지원 세부 사항을 정확히 파악하여 명확하고 간결한 요약을 제공합니다.

- 제한 사항
1. 텍스트 복잡성:  라마의 문서 요약기는 명확하게 구조화된 문서에서 가장 잘 작동합니다. 모호하거나 제대로 정리되지 않은 내용으로 인해 어려움을 겪을 수 있습니다.
2. 도메인 지식: 다른 NLP 모델과 마찬가지로 특정 분야에 대한 전문 용어와 지식에 따라 성능이 달라질 수 있습니다.
3. 맥락적 고려:  일부 정보는 문맥이나 뉘앙스에 따라 다르며, 모델이 이러한 세부 정보를 완전히 포착하지 못할 수도 있습니다.

- Llama 3.1의 이미지인식 기능 작동방식

- Llama 3.1의 이미지인식 기능 작동원리



- 주요 기능

1. 멀티모드 입력 지원: 이미지 인식 기능은 다양한 형식의 이미지(JPEG, PNG, GIF)를 허용하며 사용자가 URL을 업로드할 수도 있습니다.
2. 객체 감지 및 분류:  사용자는 라마에게 "이 사진에서 모든 개 찾기"와 같이 특정 개체를 식별하도록 요청할 수 있습니다.
3. 맥락적 이해: 라마는 이미지를 분석할 때 전반적인 장면이나 맥락을 고려하므로 다음과 같은 작업에 더 적합합니다.
	- 이미지 분류
	- 객체 분류
4. 대화 인터페이스: 사용자는 자연어 인터페이스를 통해 상호 작용하여 이미지에 대한 질문을 쉽게 할 수 있습니다.
