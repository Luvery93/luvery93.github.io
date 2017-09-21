---
layout: post
title: "정보보안기사 개인 정리 03 - 대칭키 암호"
categories: [정보보안기사]
date: 2017-08-29 14:31 +09:00
comments: true
---

### 대칭키 암호

#### 현대 대칭키 암호

1. 현대 블록 암호
   * 개요
     * 대칭키 블록 암호는 k비트 키를 사용하여 n-비트 평문 블록을 암호화하거나 n-비트 암호문을 복호화한다.
     * 복호화 알고리즘은 암호 알고리즘의 역함수이다.
     * 메시지의 길이가 n비트보다 작다면 n비트 블록을 만들기 위해 패딩(padding)이 추가된다.
   * 치환(Substitution)과 전치(Transposition)
     * 블록 암호는 비트단위의 치환 혹은 전치 암호로 동작된다.
     * 치환암호에서 평문과 암호문의 0과 1의 비트 개수는 다르다.
     * 전치암호에서 메시지의 길이가 n일 떄, 평문 혹은 암호문의 개수는 2^n이다.
     * 현대블록암호는 전수공격을 예방하고자 치환암호로 설계된다.
   * 현대 블록 암호의 구성 요소
     * 이동요소(Shift) + 교환요소(Swap) + 분할요소(Split) + 조합요소 + 전치 장치(P-Box) + 치환 장치(S-Box) + XOR 연산(exclusive-OR)
     * 혼돈과 확산의 성질을 만족시킨다.
   * P-박스
     * 단순 P-박스 : 전치 과정을 병렬적을 수행한다. 역함수가 존재한다.
     * 축소 P-박스 : n비트를 입력 받아 m비트를 출력한다. (단, n > m)
     * 확장 P-박스 : n비트를 입력 받아 m비트를 출력한다. (단, n<m)
   * S-박스
     * 치환 암호의 축소 모형으로 입력 비트와 출력 비트가 같은 경우에만 역함수가 존재한다.
   * 합성 암호(Product Ciphers)
     * Shannon은 치환, 전치, 그리고 기타 요소를 결합한 합성 암호를 소개하였다.
     * 혼돈(confusion)은 암호문과 키의 관계를 숨기는 것
     * 확산(diffusion)은 평문의 통계적 성질을 숨기는 것, 평문과 암호문의 관계를 숨기는 것
   * 라운드(Rounds)
     * 반복적인 합성 암호를 라운드라고 하며 이를 통해 확산과 혼돈 성질을 얻는다.
   * 두가지 종류의 합성 암호
     1. Feistel 암호
        * 자기 자신을 역으로 갖는 것, 역함수가 존재하는 것, 역함수가 존재하지 않는 것의 세 가지 구성요소로 이루어진다.	
        * 3라운드 이상의 짝수 라운드로 구성되며 라운드 수의 관계 없이 복호화가 가능하다. 즉, 암호화/복호화 과정이 같다.
        * DES, LOKI, CAST, Blowfish, MISTY, RC5, RC6, CAST256, E2, Twofish, Mars
     2. Non-Feistel 암호
        * 역함수가 존재하는 것만 구성요소로 이루어진다.
        * 즉, 동일한 입출력 비트수를 가지는 S-박스와 단순 P-박스만 허용된다.
        * SPN : SAFER, IDEA, SHARK, Square, SRYPTON, Rijndael, SAFER+, Serpent
2. 현대 스트림 암호
   * 개요
     * 스트림 암호는 한번에 r비트를 생성한다. 평문 비트 스트림, 암호문 비트 스트림, 키 비트 스트림의 길이가 각각 r이다.
     * 블록 암호보다 빠르며 하드웨어 구현 또한 블록 암호보다 용이하다.
   * 동기식 스트림 암호
     * 키 스트림은 평문 혹은 암호문 스트림과 독립적
     * One-Time Pad
       * 암호화를 수행할 떄마다 랜덤하게 생성된 키 스트림을 이용한다.
       * 샤논에 의해 수학적으로 무조건 안전(unconditionally secure)하고 해독 불가능(theoretically unbreakable)하다고 증명되었다.
       * 암/복호화 알고리즘은 배타적논리합 연산이 한 비트씩 적용된다.
     * 귀환 쉬프트 레지스터(Feedback Shift Register)
       * 쉬프트(Shift) 레지스터와 귀환(Feedback) 함수로 구성된다.
     * 선형 귀환 쉬프트 레지스터(LFSR, Linear Feedback Shift Register)
     * 비선형 귀환 레지스터(NLFSR, Nonlinear Feedback Shift Register)
   * 비동기식 스트림 암호
     * 키 스트림의 각 비트는 이전의 평문이나 암호문에 종속적으로 결정된다.
     * 블록 암호에서 CFB 모드는 실제로 비동기식 스트림 암호를 생성한다.

#### DES(Data Encryption Standard)

1. 개요
   * 미국 국립기술표준원(NIST) 에서 국가적으로 사용할 대칭키 암호시스템으로 채택되었으며, 이후 삼중 DES도 채택됨
2. DES 구조
   * 평문의 길이 : 64비트
   * 키의 길이: 56비트, 7비트마다 오류 검출을 위한 정보가 1비트씩 포함되어 있음
   * 라운드 : 16 회
     * Feistel 암호
     * 56비트 키에서 16개의 48비트의 라운드키를 만들어 각각의 라운드에 사용
     * 라운드 마다 2개의 혼합기(mixer)와 교환기(swapper)가 존재
     * 교환기는 역함수 구성요소로 역연산이 가능
   * P-박스 : 2개
     * 초기 전치(initial permutation)에 이전 출력 값을 입력으로 받음
     * 최종 전치(final permutation)에 다음 라운드에 입력될 출력 생성
   * S-박스 : 8개, 비선형 함수로 구성 됨
   * DES 함수 
     * 확장 P-박스, 키 XOR, 8개의 S-박스, 단순-P박스 4부분으로 이루어짐
   * 암호화 알고리즘과 복호화 알고리즘
     * 암호화 알고리즘에서 라운드 서브키의 순서와 복호화 알고리즘에서 라운드 서브키의 사용순서는 역순이다.
3. DES 분석
   * 설계 기준
     * S-박스
       * 각 라운드에서부터 다음 라운드까지 혼돈과 확산 성질을 만족해야 함
       * 비선형 함수
       * 입력 값을 한비트 바꾼다면 두 비트 이상의 값이 바뀐다
     * P-박스
       * 단순 P-박스(최종 전치), 확산 P-박스(초기 전치) 모두 비트들을 확산시킨다.
     * DES 취약점
       * 키의 크기가 56비트로 작은 것이 취약점
4. 삼중 DES
   * 두 개의 키를 갖는 삼중 DES
     * 암호화 과정의 첫 번쨰 단계와 세 번째 단계에서 암호화 알고리즘을 사용하고 키가 같다.
     * 암호화 과정의 두 번쨰 단계에서 복호화 알고리즘을 사용하고 다른 키를 사용한다.


   * 세 개의 키를 갖는 삼중 DES
     * 암호화 과정의 첫 번쨰 단계에서 세번 쨰 단계에서 암호화 알고리즘을 사용한다.
     * 암호화 과정의 두 번째 단계에서 복호화 알고리즘을 사용하며 키는 모두 다르다.
   * DES와의 호환성
     * 3DES의 키를 모두 같은 것으로 정하면 DES에 대한 상호 호환성을 지닌다.

| 구분              | DES  | Triple DES | AES              |
| --------------- | ---- | ---------- | ---------------- |
| 평문 블록 크기(bits)  | 64   | 64         | 128              |
| 암호문 블록 크기(bits) | 64   | 64         | 128              |
| 키 크기(bits)      | 56   | 112 또는 168 | 128, 192, 또는 256 |

#### AES

1. 개요
   * NIST에서 DES를 대체하기 위해 AES(Advanced Encryption Standard)를 공모함
   * 128비트의 블록 크기와, 128, 192 또는 256비트의 세가지 키 크기를 가지는 공개 알고리즘이 조건
   * MARS, RC6, Rijndael, Serpent, Twofish -> Rijndael(레인달)이 채택
   * 안전성(security), 비용(cost), 구현 효율성(implementation)이 선정 기준(Criteria)
   * 라운드(Rounds)
     * 128비트 평문을 128비트 암호문으로 출력하는 Non-Feistel 알고리즘
     * AES-128(10라운드), AES-192(12라운드), AES-256(14라운드)
2. 암호(CHIPHERS)
   * 레인달에서는 SPN(Substitution-Permutation Network)구조를 이용
     * 구성 요소가 역변환이 가능해야하는 제약사항이 있지만 더 많은 병렬성을 제공
     * 입력을 여러개의 소블럭으로 나누어 S-box에서 치환하고 P-box에서 전치하는 과정을 반복
   * S-box를 이용한 치환, 행이동, 행연산을 이용한 열변환, 키연산을 통한 열변환의 4가지 기본연산

#### 기타 대칭키 암호 알고리즘

1. IDEA(International Data Encryption Algorithm)
   * 64비트의 블록 크기, 128비트의 키 크기, 8라운드
   * DES 보다 2배 효율적
2. SEED
   * 한국정보진흥원 개발, TTA, ISO/IEC, IETF 국제 블록 알고리즘 표준으로 제정
   * 128비트의 블록크기, 128비트의 키에서 16개의 64 라운드키 생성, 16라운드
   * 변형된 Feistel 구조
3. ARIA(Academy Research Institue Agency)
   * 국가보안기술연구소(NSRI) 주도로 Academy(학계), Research Institue(연구소), Agency(정부기관) 공동 개발
   * 128비트의 블록크기, 128, 192, 256비트의 키 크기

#### 현대 대칭키 암호를 이용한 암호화 기법

1. 현대 블록 암호의 사용
   * ECB 모드 : Electric CodeBook mode(전자 부호표 모드)
     * 평문을 n비트의 블록으로 분할하여 암호화를 수행
     * 마지막 블록은 다른 블록과 같은 크기로 만들기 위해 패딩이 필요할 수 있음
     * 암호문 블록이 독립성을 지니므로 매우 많은 데이터베이스를 암호화할때 병렬적으로 처리할 수 있음
   * CBC 모드 : Cipher Block Chaining mode(암호 블록 연쇄 모드)
     * 초기 벡터(IV) 그리고 이전 단계의 암호화된 블록이 다음 블록과 XOR 되어 암호화를 수행
     * 암호화 과정에서 평문 블록의 한 비트의 오류는 모든 암호화 블록에 영향을 미치며 복호화 과정에서 암호문 블록 1개의 파손은 2 개의 평문 블록에 영향을 미친다.
     * IPSec, 3DES-CBC, AES-CBC, Kerberos version 5
   * CFB 모드 : Cipher-FeedBack mode(암호 피드백 모드)
     * DES와 AES와 같은 모든 블록 암호를 스트림 암호로 바꾼 비동기식 스트림 암호이다.
   * OFB 모드 : Output-FeedBack mode(출력 피드백 모드)
     * CFB 모드와 비슷하나 키스트림이 이전 암호문 블록이 아닌 초기화 벡터(IV)의 이전 값에 종속적이고 암호문 블록은 각각 독립적이다.
     * 다시 말해 키스트림은 평문이나 암호문에 독립적이므로 동기식 스트림 암호이다.
   * CTR 모드 : CounTeR mode(카운터 모드)
     * 독립적인 키스트림을 사용하지만 피드백을 사용하진 않는다, 서로 다른 키로 XOR되는 스트림 암호이다.
     * 키 스트림의 의사난수성은 카운터를 사용함으로써 해결한다.
     * 카운터의 초기값은 암호화 때마다 비표(다른 값, nonce)를 기초로해서 생성된다.
     * ATM(asynchronous transfer mode) 네트워크 보안과 IPSec(IP security)에 응용이 된다.
2. 블록 암호 공격
   * 차분공격에 대한 기본 개념(Differential Cryptanalysis)
     * 선택 평문 공격법, 두 개의 평문 블록들의 비트 차이에 대응되는 암호문 블록들의 비트차이를 이용하여 키를 찾아내는 방법
   * 선형공격에 대한 기본개념(Lineaer Cryptanalysis)
     * 알려진 평문 공격법, 알고리즘 내부의 비선형 구조를 적당히 선형화시켜 키를 찾아내는 방법
   * 전수공격법(Exhaustive key search)
     * 암호화할 떄 일어날 수 있는 가능한 모든 경우를 조사하는 방법
   * 통계적 분석(Statistical analysis)
     * 암호문에 대한 평문의 각 단어의 빈도에 관한 통계적 성질을 이용하는 방법
   * 수학적 분석(Mathematical analysis)
     * 통계적인 방법을 포함하여 수학적 이론을 이용하여 해독하는 방법