---
layout: post
title: "정보보안기사 개인 정리 04 - 비대칭키 암호"
categories: [정보보안기사]
date: 2017-08-29 16:56 +09:00
comments: true
---

### 비대칭키 암호

#### 비대칭키 암호

1. 키 배송 문제
   * 대칭키 암호 사용에는 키 배송 문제(key distribution problem)이 발생한다.
   * 키의 사전 공유에 의한 해결
     * 안전한 방법으로 키를 사전에 건네어 해결하는 방법
     * 인원이 많아지면 통신을 위한 키가 방대해 진다 = n(n-1)/2 개의 키가 필요
   * 키배포 센터에 의한 해결
     * 키배포 센터(KDC, key distribution center)라는 신뢰받는 제 3자에 의뢰해서 개인과 키배포 센터 사이에서만 키를 사전에 공유하는 방법
     * 키배포 센터에는 통신 인원 수 많큼의 키가 존재한다 = n 개의 키가 필요
     * 배포 순서
       * 키배포 센터에 통신을 위한 키요청을 한다.
       * 키배포 센터는 의사난수 생성기를 통해 세션키를 생성하고 통신 주체 각자의 키를 통해 세션키를 암호화하여 통신 대상에게 보낸다.
       * 통신 주체는 자신의 키로 세션키를 복호화하여 통신한다.
       * 통신이 끝나면 세션키를 삭제한다.
   * Diffie-Hellman 키 교환에 의한 해결
     * 최초의 비밀키 교환 프로토콜로 공개키 암호화방식의 개념을 이용하였다.
     * 유한체상의 이산대수문제를 풀기 어렵다는 사실이 Diffie-Hellman 키 교환을 뒷받침한다.
     * 실제로는 공유할 키를 계산해여 만들어내므로 Diffie-Hellman 키합의(key agreement)라고도 한다.
     * 비밀키가 노출되더라도 그 후의 키 분배 과정을 통해 얻는 세션키의 안전성에 영향을 미칠 수 없는 완전 순방향 비밀성(perfect forward secrecy) 특성을 지닌다.
     * 절차
       * 300자리나 넘는 매우 큰 소수 p(1024비트)와 1 < g < p-1을 만족하는 정수 g를 통신 주체간에 공유한다.
       * 통신 주체는 정수 x, y를 각자 선택하여 g^x mod p(R1), g^y mod p(R2)를 구한다.
       * 통신 주체는 R1, R2를 상대방에게 보내고 자신이 선택한 정수로 (R2)^x mod p, (R1)^y mod p를 계산하는데 이것이 두 통신주체사이의 키가 된다.
     * 안전성
       * 이산대수 공격
         * 공격자는 R1, R2, p, g를 알 수 있기 때문에 R1, R2로 부터 x,y를 구할 수 있다면 비밀키의 역할을 하지 못한다.
       * 중간자 공격(main-in-the-middle attack)
         * 통신 주체간의 인증단계가 없으므로 공격자와 통신주체들 간의 키교환을 진행할 수 있다.
         * 국-대-국 프로토콜(station-to-station protocol)은 통신 주체간의 세션키를 만들기 위해 공개키 인증서를 이용한 디지털서명을 사용하여 중간자 공격을 막을 수 있다.
   * 공개키 암호에 의한 해결
     * 통신 주체는 암호화키(공개키)를 송신자에게 알려 암호화된 정보를 자신의 복호화키(비밀키)를 통해 복호화하여 키를 교환한다.

2. 공개키 암호(public-key cryptography)
   * 공개키 암호는 수학적으로 해결하기 곤란한 문제를 토대로 기밀성을 유지하며 전자문서의 무결성과 부인방지 기능을 가진다.
   * 암호화키(공개키), 복호화키(개인키는) 한 쌍으로 분리되어 있다.
   * RSA는 공개키 암호의 De Facto Standard(사실 표준)이다.
   * 비대칭키 암호시스템의 개인키는 하나 혹은 그 이상의 숫자들로 이루어져있다.
   * 암호 시스템의 비대칭성을 강조하는데 이는 보안성을 제공하는 책임이 대부분 수신자 측에 있다는 것이다.
   * 취약점
     * 공개키 암호에 의해 키 배송 문제가 해결되었으나, 공개키 자체가 올바른 공개키인지 확인할 방법이 없다. 
     * 공개키에 대한 신뢰성 문제는 인증 과정이 없을 경우 중간자 공격에 다시 취약해진다.
     * 관용 암호시트템과 비교했을 떄 암호화 시간이 매우 오래 걸린다.

3. RSA 암호시스템
   * 인수분해 문재해결의 높은 난이도를 이용한 공개키 알고리즘의 de facto(사실상 표준)로 암호화뿐만 아니라 디지털서명의 용도로도 사용된다.
   * 표기법
     * p, q : 매우 큰 서로 다른 소수, 비공개
     * n : p x q, 공개키
     * φ(n) : (p-1)(q-1)
       * 오일러 피(토션트) 함수는 φ(n)은 n과 n보다 작은 자연수중 서로소의 개수
       * n 이 소수 일 경우 φ(n) = n-1
       * n = p x q 일 떄, φ(n) = φ(p) x φ(q) = (p-1)(q-1)
     * e : φ(n)보다 작고 서로소인 수, 공개키
     * d : de mode φ(n) = 1 인 수, 비밀키(개인키)
       *  모듈러 연산의 곱의 역원
       * 최대 공약수가 1인 수, gcd(e, d) = 1, 확장 유클리드 호제법 사용
   * 암호화와 복호화
     * 암호문 : C = P^e mod n
     * 평문 : P = C^d mod n
     * 통신 주체는 상대방의 공개키로 평문을 암호화하여 송신하고 수신자는 자신의 개인키로 암호문을 복호화하여 평문을 획득한다.
   * 취약점
     * 소인수분해 공격 : 현실적인 시간 내에 효율적인 소인수분해 알고리즘이 개발되면 RSA는 무용지물
     * 중간자 공격 : 통신 주체사이에서 RSA를 하는 공격자가 존재
   * 권장사항
     * n의 비트수는 1024비트 이상이며 2^1024근방에 있는 수 이거나 309자리의 십진수가 되어야한다.
     * p, q는 512비트 이상이며, 2^512 근방에 있거나 154자리의 십진수가 되어야한다. 또 한 너무 가까이 있는 수이면 안된다.
     * p-1, q-1은 적어도 하나의 큰 소인수를 가지며, 최대공약수가 작아야 한다.
     * e는 2^16+1에 가까워야 하고 개인키(d)가 노출당했다면 전부 변경해야한다.
     * 메시지는 OAEP를 사용하여 패딩되어야 한다.
   * 최적 비대칭키 암호 패딩(OAEP, optimal asymmetric encryption padding)
     * 짧은 메시지는 짧은 메시지 공격에 취약하므로 패딩을 추가해야 한다.

4. Rabin 암호 시스템

   * RSA와 비슷하나 2차 합동에 근거한 암호시스템이다.
   * 오직 한 번의 곱셈으로 이루어져 있어 성능이 낮은 플랫폼에서 활용된다.
   * p, q가 충분히 크다면 RSA만큼이나 안전하다. 수학적인 복잡도가 동일하다.
   * 오픈 소스

5. ElGamal 방식

   * RSA와 비슷하나 이산대수 문제를 근거해서 만들어진 암호시스템이다.
   * 암호문의 길이가 평문의 2배가 되는 단점이 있다.
   * GnuPC에 구현

6. 타원 곡선 암호(ECC, elliptic curve cryptosystem)

   * 타원곡석(elliptic curve)이론에 근거한 암호 시스템으로 키의 길이가 RSA와 ElGamal보다 짧다. ECC의160비트 키는 RSA의 1024비트의 키와 동일한 보안수준을 가진다.
   * 전자상거래의 핵심기술이다.

   | 항목   | ECC 방식       | RSA 방식         |
   | ---- | ------------ | -------------- |
   | 기반구조 | WPKI(무선)     | PKI(유선)        |
   | 속도   | 우수           | 느림             |
   | 키 크기 | 상대적으로 작은 키   | ECC에 비해 큰 키    |
   | 적용   | 소형 Mobile 환경 | 인프라가 다소 구현된 환경 |

7. 대칭키 방식과 비대칭키 방식의 비교

   | 항목      | 대칭키                  | 공개키           |
   | ------- | -------------------- | ------------- |
   | 키의 상호관계 | 암호화키 = 복호화키          | 암호화키 ≠ 복호화키   |
   | 안전한 키길이 | 128비트 이상             | 2048비트 이상     |
   | 암호화키    | 비밀                   | 공개            |
   | 복호화키    | 비밀                   | 비밀            |
   | 비밀키 전송  | 필요                   | 불필요           |
   | 키 개수    | N(N-1)/2             | 2N            |
   | 암호화 속도  | 고속                   | 저속            |
   | 경제성     | 높다                   | 낮다            |
   | 제공 서비스  | 기밀성                  | 기밀성, 부인방지, 인증 |
   | 목적      | 데이터(파일) 암호화          | 대칭키 교환        |
   | 전자서명    | 복잡                   | 간단            |
   | 단점      | 키 교환 원리가 없다          | 중간자 공격에 취약    |
   | 해당 알고리즘 | DES, 3DES, AES, IDEA | RSA, ECC, DSA |

#### 하이브리드 암호시스템

1. 대칭키 암호화 공개키 암호
   * 공개키 암호시스템은 대칭키 암호시스템의 키 배송 문제를 해결할 수 있으나 공개키 암호시스템 자체가 중간자 공격에 취약한 문제를 해결해야 한다.
   * 하이브리드 암호시스템은 공개키 암호시스템의 공개키에 대한 인증을 진행할 수 있는 암호시스템이다.
2. 하이브리드 암호 시스템(hybrid cryptosystem)
   * 의사난수 생성기, 대칭키 암호, 공개키 암호를 합친 암호시스템이다.
   * 세션키(대칭키)로 메시지를 암호화하여 기밀성을 유지한다.
   * 세션키는 의사난수 생성기로 생성되며 공개키 암호를 통해 암호화된다.
   * 암호 소프트웨어인 PGP, 암호통신에 사용되는 SSL/TLS 등이 있다.
   * PGP에는 디지털서명, 디지털서명의 검증, 개인키의 관리도 추가되어 있다.