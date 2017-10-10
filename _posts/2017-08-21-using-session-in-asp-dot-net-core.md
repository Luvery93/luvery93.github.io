---
layout: post
title: "ASP.NET Core 1.x Session 이용"
date: 2017-08-21 15:42 +09:00
categories: [Development]
comments: true
---

### 사전 준비

* 이 포스트는 2017-08-21, ASP.NET Core 1.1 기준으로 작성되었습니다.
* Windows, Visual Studio 2017 환경에서 작성되었습니다.
* 이 포스트는 [asp.net core docs - ASP.NET Core - Session and application state](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/app-state)를 기준으로 작성되었습니다.
  1. [.NET SDK](https://www.microsoft.com/net/core#windowscmd)가 설치되어 있지 않는 경우 설치합니다.
  2. [Visual Studio](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=community&rel=15)가 설치되어 있지 않는 경우 설치합니다.

---

* **도구 - NuGet 패키지 관리자 - 솔루션용 NuGet 패키지 관리**를 선택합니다.

  ![1]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/1.png)

* **Microsoft.AspNetCore.Session**을 검색하여 **1.x** 버전을 다운로드 합니다. 현재 asp.net core가 2.x preview에 있으므로 본 프로젝트와 호환이 되지 않아 버전에 맞게 설치합니다.

  ![2]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/2.png)

* **Startup.cs** 파일에 세션 관련 설정을 추가합니다.

  ```c#
  services.AddSession(options =>
  {
  	options.IdleTimeout = TimeSpan.FromHoures(10); // 세션 만료 시간, 10시간
  	options.CookieHttpOnly = true;
  });
  ```

  ![3]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/3.png)

  ```c#
  app.UseSession();	![4]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/4.png)
  ```

  ![4]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/4.png)

* 컨트롤러에서 세션을 사용할 경우 **ISession** 객체를 가져옵니다.

  ```c#
  private readonly IHttpContextAccessor _httpContextAccessor;
  private ISession _session => _httpContextAccessor.HttpContext.Session;

  public Controller(IHttpContextAccessor httpContextAccessor)
  {
  	_httpContextAccessor = httpContextAccessor;
  }
  ```

  ![5]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/5.png)

* 세션 값을 추가하려면 **SetString, SetInt32** 메소드를 이용합니다.

  ![6]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/6.png)

* 뷰페이지를 위해 세션 키값을 반환합니다. 이 떄 반환 형식은 **IEnumerable&lt;String&gt;** 입니다.

  ![7]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/7.png)

* 세션 값을 삭제하려면 **Clear** 메소드를 이용합니다.

  ![8]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/8.png)

* 예제 뷰 페이지를 생성합니다. **ASP.NET Core - 웹 - ASP.NET - MVC 뷰 페이지**를 생성합니다.

  ![9]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/9.png)

* 항목 6번에서 보낸 Key값은 **IEnumerable&lt;String&gt;** 이므로 **Model**의 형식을 설정하여 줍니다.

  ![10]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/10.png)

* 세션 객체인 **ISession**을 뷰페이지에서 그대로 사용하려면 아래 처럼 injection 코드를 작성합니다.

  ```html
  @using Microsoft.AspNetCore.Http;
  @inject IHttpContextAccessor _httpContextAccessor

  @{
  	ISession _session = _httpContextAccessor.HttpContext.Session;
  }
  ```

  ![11]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/11.png)

* **Index 페이지를 거쳐 SessionTest 페이지**로 접근하였을 떄 결과입니다.

  ![12]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/12.png)

* **세션 Clear를 위해 SessionReset 페이지**로 접근하였을 떄 결과입니다.

  ![13]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/13.png)

  ![14]({{ site.url }}/img/2017-08-21-using-session-in-asp-dot-net-core/14.png)