---
layout: post
title: "정보보안기사 개인 정리 01 - 정보보호관리의 개념"
categories: [정보보안기사]
date: 2017-08-27 00:46 +09:00
comments: true
---

### 정보보호관리의 개념

#### 정보화 사회의 정보보호

1. 정보사회의 특성과 역기능
   * 정보사회의 특성 : 비대면성, 익명성, 시간 및 공간적 운영의 무제한성, 무제한적인 정보 및 신속한 전송, 미래의 범죄 및 전쟁 공간
   * 정보화 역기능 : 개인의 프라이버시 침해, 해커와 바이러스의 기승, 불법적인 위변조를 통한 범죄, 정보시스템의 파괴로 의한 사회마비
2. 정보보호(Information Security)
   1. 정의
      * 정보보호(information security)는 정보의 수집, 가공, 저장, 검색, 송신, 수신 중에 발생하는 정보의 훼손, 변조, 유출 등을 방지하기 위한 관리적, 기술적 수단 또는 그러한 수단으로 이루어지는 행위이다.
      * 정보보호는 기밀성, 무결성, 가용성, 인증성 및 부인방지를 보장하기 위한 기술적, 물리적, 관리적 보호대책을 강구하는 것이다.
      * 정버보호 시스템에는 정보보호 관리, 컴퓨터 및 데이터 보안, 네트워크 보안과 정보보호 정책이 포함된다.
   2. 정보의 가용성과 안정성(보안성)
      * 정보의 가용서과 보안 측면에서 보면 정보보호란 정보의 활용과 정보의 통제 사이에서 균형감각을 갖는 행위이다.
      * 정보의 가용성을 극대화하자는 정보의 활용과 위협 요소를 줄이고 안정성을 확보하기 위해 최대한 통제하자는 정보의 통제사이에서의 균형점을 찾아야한다.
   3. 정보보호의 목표
      1. 기밀성(Confidentiality)
         * 오직 인가된(authorized) 사람, 인가된 프로세스, 인가된 시스템만이 알 필요성(Need-to-know)에 근거하여 시스템에 접근해야 한다는 원칙
         * 데이터 기밀성 : 개인 정보나 기밀 정보를 부정한 사용자가 이용하거나 그들에게 노출되지 않도록 하는 것.
         * 프라이버시 : 개인과 관련된 어떤 정보가 수집되고 저자되는지, 누구에게 그 정보가 공개되는지, 누가 공개하는지 등을 통제하거나 영향이 미칠 수 있도록 하는 것
         * 접근 제어, 암호화
      2. 무결성(Integrity)
         * 네트워크를 통해 송수신되는 정보의 내용이 불법적으로 생성 또는 변경되거나 삭제되지 않도록 보호되어야 하는 성질
         * 무결성 왜곡이 항상 악의적인 행동의 결과로 나타나는 것이 아니라 전력차단과 같은 시스템 중단이 정보에 예쌍치 못한 변형을 일으킬 수 있다.
         * 접근 제어, 메시지 인증, 침입탐지, 백업
      3. 가용성(Availability)
         * 시스템이 지체 없이 동작하도록 하고, 합법적 사용자가 서비스 사용을 거절당하지 않도록 하는 것
         * 인가된 자가 정보에 접근할 수 없는 비가용성은 조직에 있어 기밀성이나 무결성의 부족만큼 해롭다.
         * 데이터의 백업, 중복성의 유지, 물리적 위협요소로부터의 보호


#### 정보보호 관리

1. 정보보호 관리

   * 정보는 기업이나 공공기관의 중요한 자산 중 하나로서, 의도하지 않는 비인가자에게 노출되거나 갈취당하게 되면 위험을 초래할 수 있으므로 관리되어야 한다.

2. 정보보호 관리와 정보보호 대책

   * 관리적 보호대책 -> 물리적 보호대책 -> 기술적 보호대책

   1. 기술적 보호대책
      * 정보 시스템, 통신망, 정보(데이터)를 보호하기 위한 접근통제, 암호기술, 백업 체계, 정보시스템 자체에 보안성이 강화된 시스템 소프트웨어를 사용하는 방식
   2. 물리적 보호대책
      * 화재, 수해, 지진, 태풍 등과 같은 자연재해로부터 정보시스템이 위치한 정보처리 시설을 보호하기 위한 자연재해 대책과 불순 세력이나 적의 파괴로부터 정보시스템을 보호하기위한 출입통제, 시건(잠금) 장치 사용
   3. 관리적 보호대책
      * 법, 제도, 규정, 교육 등을 확립하고 보안계획을 수립하고 이를 운영(보안등급, 엑세스 권한)하며, 위험 분석 및 보안감사를 시행하여 정보시스템의 안전성과 신뢰성을 확보하기 위한 대책이다.
      * 조직체의 정보보호를 효과적으로 보장하기 위해서는 다양한 기술적 보호대책 뿐만 아니라 이들을 계획하고, 설계하며, 관리하기 위한 제도, 정책, 절차 등의 괄리적 보호대책도 매우 중요하다. 특히, 내부자의 부당행위를 방지하기 위한 교육은 무엇보다 중요하게 취급되어야 한다.

#### OSI 보안구조

1. 기본 개념

   * ITU-T 권고안 X.800, OSI 보안 구조는 관리자가 효과적으로 보안 문제를 조직화 할 수 있는 유용한 방법을 제공한다.
   * 보안 공격(Security attack) : 기관이 소유한 정보의 안전성을 침해하는 제반 행위
   * 보안 메커니즘(Security mechanism) : 보안 공격을 탐지, 예방하거나 공격으로 인한 침해를 복구하는 절차
   * 보안 서비스(Security service) : 조직의 정보 전송과 데이터 처리 시스템의 보안을 강화하기 위한 처리 또는 통신 서비스, 이 서비스는 보안 공격에 대응하기 위한 것이며, 하나 또는그 이상의 보안 메커니즘을 사용하여 서비스를 제공한다.

2. 보안 공격(Security attack)

   1. 기밀성을 위협하는 공격

      1. 스누핑(Snooping)
         * 데이터에 대한 비인가 접근 또는 탈취를 의미한다. 인터넷으로 전송되는 파일은 기밀 정보를 담고 있을 수 있는데, 비인기자가 이를 가로채고 자신의 이익을 위하여 그 내용을 사용할 수 있다.
      2. 트래픽분석(Traffic Analysis)
         * 데이터를 암호화하여 도청자가 그 데이터를 이해할 수 없게 해도 도청자는 트래픽을 분석함으로써 다른 형태의 정보를 얻을 수 있다. 예를 들어, 도청자는 수신자 또는 송신자의 전자 주소를 알아 낼 수 있으며, 전송의 성향을 추측하는데 도움이 되는 질의와 응답의 쌍들을 알 수 있다.

   2. 무결성을 위협하는 공격

      1. 변경(메시지 수정, Modification)
         * 적법한 메시지의 일부를 불법으로 수정하거나 메시지 전송을 지연시키거나 순서를 뒤바꾸어 인가되지 않는 효과를 노리는 행위
      2. 가장(Masquerading)
         * 한 개체가 다른 개체의 행세를 하는 것이다. 이 공격은 다른 형태의 적극적 공격과 병행하여 수행한다.
      3. 재연(재전송, Replaying)
         * 적극적 공격의 하나로, 획득한 데이터 단위를 보관하고 있다가 시간이 경과한 후에 재전송함으로써 인가되지 않은 사항에 접근하는 효과를 노리는 행위
      4. 부인(Repudiation)
         * 메시지의 송신자는 차후에 자신이 메시지를 보냈다는 것을 부인할 수 있고, 메시지의 수신자는 차후에 메시지를 받았다는 것을 부인할 수 있다.

   3. 가용성을 위협하는 공격

      1. 서비스 거부(Denial of Service)
         * 서비스 거부(Dos)는 매우 일반적인 공격으로 시스템의 서비스를 느리게 하거나 완전히 차단시키는데 다양한 전략을 사용할 수 있다.

   4. 소극적 공격과 적극적 공격

      * 보안 공격은 X.800과 RFC 2828에 따라 분류하면 소극적 공격과 적극적 공격으로 나눌 수 있다.
      * 소극적 공격의 목표는 단지 정보를 획득하는 것이다. 정보의 노출은 메시지의 송신자나 수신자에게 해를 끼칠 수 있지만 시스템은 영향을 받지 않는다.
      * 적극적 공격은 데이터를 바꾸거나 시스템에 해를 입힐 수 있다. 다양한 방법으로 공격을 하기 때문에 방어하기보다는 탐지하는 것이 더 쉽다.

      | Attack                    | Passive/Active | Threatening     |
      | ------------------------- | -------------- | --------------- |
      | Snooping(스누핑)             | Passive        | Confidentiality |
      | Traffic analysis(트래픽 분석)  | Passive        | Confidentiality |
      | Modification (변경, 수정)     | Active         | Integrity       |
      | Masquerading(가장)          | Active         | Integrity       |
      | Replaying(재연, 재전송)        | Active         | Integrity       |
      | Repudiation(부인)           | Active         | Integrity       |
      | Denial of service(서비스 거부) | Active         | Availability    |

3. 보안서비스(security service)

   * X.800에서 보안 서비스란 시스템의 적절한 보안이나 데이터 전송의 보안을 보장하는 통신 개발 시스템의 프로토콜 계층에 의해서 제공되는 서비스이다. 보안 정책을 구현하고 보안 메커니즘에 의해서 구현된다.

   1. 기밀성(Confidentiality)
      * 기밀성이란 소극적 공격으로부터 데이터를 보호하는 것을 뜻한다.
   2. 무결성(Integrity)
      * 기밀성 서비스처럼 무결성 서비스도 메시지 스트림, 단일 메시지, 메시지 안의 선별된 필드에 적용될 수 있다.
   3. 가용성(Availability)
      * X.800과 RFC 2828에서 가용성이란 인가된 시스템이 자원에 접근할 필요가 있거나 사용하고자 할 떄 시스템의 성능에 따라 시스템 자원에 접근할 수 있도록 하는 것을 말한다.
   4. 인증(Authentication)
      * 연결지향(connection-oriented) 통신에서 연결 성립 시 송신자 또는 수신자에 대한 인증(peer entity authentication)을 제공하고, 비연결지향(connectionless) 통신에서는 데이터의 출처를 인증한다.(data origin authentication)
      * 대등 개체 인증(Peer entity authentication) : 통신하는 상대방의 신원을 확인시켜준다.
      * 데이터 출처 인증(Data origin authentication) : 데이터 단위의 출처에 대한 확인을 할 수 있다.
   5. 부인방지(부인 봉쇄, Nonrepudiation)
      * 부인 봉쇄란 송신자나 수신자 양측이 메시지를 저송했거나 수신한 사실 자체를 부인하지 못하도록 막는 것을 말한다.
   6. 접근제어(Access Control)
      * 네트워크 보아넹서 접근제어란 통신 링크를 통한 호스트 시스템과 응용 간의 접근을 제한하고 통제할 수 있는 능력을 말한다.

#### 기본 보안용어 정의

* 자산(Asset)
  * 조직이 보호해야 할 대상으로서 데이터 혹은 자산 소유자(Data Owner)가 가치를 부여한 실체이다.
  * 하드웨어 : 컴퓨터 시스템과 데이터 처리, 저장, 통신 장비
  * 소프트웨어 : 운영체제, 시스템 도구, 어플리케이션
  * 데이터 : 파일, 데이터베이스, 암호 파일과 같은 보안 관련 데이터
  * 통신 설비와 네트워크 : 지역과 광역 네트워크 통신 연결, 브리지, 라우터 등

* 취약점(Vulnerability)

  * 위협의 이용대상으로 정보보호 대책이 미비한 관리적, 물리적, 기술적 약점이다.

* 위협(Threat)

  * 손실이나 손상의 원인이 될 가능성을 제공하는 환경의 집합 또는 보안에 해를 끼치는 행동이나 사건이다.
  * 가로채기(interception) : 비인가된 당사자가 자산으로의 접근을 획득한 것을 의미(불법 복사, 도청) -> 기밀성에 영향
  * 가로막음(interruption) : 시스템 자산은 손실되거나, 손에 넣을 수 없거나, 사용 불가능하게 됨(하드웨어 장치의 악의적 파괴, 파일 삭제, 서비스 거부 등) -> 가용성에 영향
  * 변조(modification) : 비인가된 당사자가 접근하여 그 내용을 변경(데이터베이스 값 변경, 특정 프로그램 변경 등) -> 무결성에 영향
  * 위조(fabrication) : 비인가된 당사자가 컴퓨팅 시스템상에 불법 객체의 위조정보를 생성 -> 무결성에 영향

* 위협원(Threat agents)

  * 정보자산에 해를 끼치는 행동을 할 수 있는 실체로 해커, 일반 사용자, 컴퓨터 프로세스, 재난 등이 있다.

* 위험(Risk)

  * 예상되는 위협에 의해 자산에 발생할 가능성이 있느 ㄴ손실의 기대치, 자산의 가치 및 취약점과 위협 요소의 능력, 보호 대책의 효과 등에 의해 영향을 받는다.
  * 위협원이 취약점을 이용하여 위협이라는 행동을 통해 자산에 악영향을 미치는 결과를 가져올 가능성으로 위험은 자산X위협X취약점으로 표현한다.

* 노출(Exposure)

  * 위협 주체에게 손실(losses)을 드러내 보이는 경우로 취약점은 발생 가능한 피해를 노출시킨다.

* 안전장치, 보안대책(Safeguard/Countermeasures)

  * 각종 위협이나 변경을 방어하거나 감소시키며 자산을 보호하는 기술, 정책 또는 절차로 예방적 수단이다.

* 잔여 위험(Residual Risk)

  * 정보보호대책을 구현한 후 남아있는 위험이다.

* 다계층 보안/심층 방어(Defense in Depth)

  * Multi Layered(Level) Security라고도 불리는 것으로, 여러 계층의 보안대책이나 대응수단을 구성하는 것이다.
  * 다계층 보안이므로 한 가지 통제가 실패하더라도 전체 시스템을 위험에 빠뜨리지 않는다.
  * 보호, 탐지, 대응으로 이루어진 보안 접근법이다.

* 직무상의 신의성실, 노력(Due Care, Due Diligence)

  * Due : 특정 목적을 위하여 필요하거나 요구되는 적절하고 충분한 의무
  * Due care : 특정 목적을 위하여 필요하거나 요구되는 충분한 주의
  * Due Diligence : 특정 목적을 위하여 필요하거나 요구되는 충분한 노력

* 사회공학(Social Engineering)

  * 인간 상호 작용의 깊은 신뢰를 바탕으로 사람들을 속여 정상적인 보안 절차를 깨트리기 위한 비기술적 침입 수단
  * 가장 약한 링크 원칙(principle of weakness link) : 보안은 가장 약한 링크보다 더 강할 수 없다. 즉, 어떤 하나의 제어수단의 실패가 전체 보안실패를 야기한다.

* 시점별 통제(Control)

  * 취약점을 감소시키거나 억제하기 위해 사용되는 메커니즘을 뜻한다.

  1. 예방통제(Preventive Control) : 사전에 위협과 취약점에 대처하는 통제
  2. 탐지통제(Detective Control) : 위협을 탐지하는 통제로, 빠른 탐지일수록 대처하기에 용이
  3. 교정통제(Corrective Control) : 이미 탐지된 위협이나 취약점에 대처하거나, 위협이나 취약점을 감소시키는 통제