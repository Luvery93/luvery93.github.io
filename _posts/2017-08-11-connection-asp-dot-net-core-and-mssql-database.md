---
layout: post
title: "ASP.NET Core MVC Database(MSSQL) 연동"
date: 2017-08-11 13:10 +09:00
categories: [Development]
comments: true
---

---

### 사전 준비

* 이 포스트는 2017-08-11, ASP.NET Core 1.1 기준으로 작성되었습니다.
* Windows, Visual Studio 2017 환경에서 작성되었습니다.
* 이 포스트는 [asp.net core docs - ASP.NET Core - Existing Database](https://docs.microsoft.com/ko-kr/ef/core/get-started/aspnetcore/existing-db)를 기준으로 작성되었습니다.

  1. [.NET SDK](https://www.microsoft.com/net/core#windowscmd)가 설치되어 있지 않는 경우 설치합니다.
  2. [Visual Studio](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=community&rel=15)가 설치되어 있지 않는 경우 설치합니다.

---

* ASP.NET Core 웹 으용 프로그램(.NET Core) 새 프로젝트를 생성합니다.

  ![1]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/1.PNG)

* 템플릿은 **웹 응용 프로그램**을 선택하며 인증 변경에서 **인증 안 함**을 선택합니다.

  ![2]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/2.PNG)

* 프로젝트가 생성 되면 **도구 - NuGet 패키지 관리자 - 패키지 관리자 콘솔**을 엽니다.

  ![3]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/3.png)

* 패키지 관리 콘솔 창에서 아래 패키지를 설치합니다.

  ```
  Install-Package Microsoft.EntityFrameworkCore.Tools

  Install-Package Microsoft.EntityFrameworkCore.SqlServer

  Install-Package Microsoft.EntityFrameworkCore.SqlServer.Degisn
  ```

  ![4]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/4.png)

* 패키지를 모두 설치하면 **프로젝트 - 종속성 - NuGet** 폴더 아래 패키지가 추가 되어있음을 확인 할 수 있습니다. 이 과정까지 진행했다면 데이터베이스에 연결할 준비가 완료되었습니다.

  ![5]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/5.png)

* 다음은 이번 포스트에 적용하고자 할 테이블 예시입니다. 

  ![6]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/6.png)

  ![7]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/7.png)

* 다시 **패키지 관리자 콘솔**에서 위에 예시로 든 데이터베이스를 C# 코드로 스캐폴딩해 옵니다. 아래 명령어를 입력합니다.

  ```
  Scaffold-DbContext "Server={Server Address};Database={Database Name};User ID={Database Auth ID};Password={Database Auth Password};" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models/{Database Name}
  ```

  ![8]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/8.png)

* 스캐폴딩이 완료되면 Models - {Database Name} 하에 Context 클래스와 테이블 캘래스들이 생성됩니다.

  ![9]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/9.png)

  ![10]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/10.png)

  ![11]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/11.png)

* 생성 된 Context 클래스의 **OnConfiguring** 함수를 삭제하고 생성자를 추가합니다.

  ```
  public MTContext(DbContextOptions<MTContext> options)
  	: base(options)
  { }
  ```

  ![13]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/13.png)

* **appsettings.json** 파일에 데이터베이스 연결 정보를 추가합니다.

  ```
  "ConnectionStrings" : {
  	"MT" : {
      	"ConnectionString" : "Server={Server Address};Database={Database Name};User ID={Database Auth ID};Password={Database Auth Password};"
  	}
  }
  ```

  ![14]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/14.png)

* **Startup.cs** 에 using 문을 추가합니다.

  ```
  using Microsoft.EntityFrameworkCore;
  using MTGlos.Models.MT;
  ```

  ![15]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/15.png)

* **Startup.cs** 의 **ConfigureServices** 함수에 아래 문장을 추가합니다.

  ```
  var MTConnection = Configuration["ConnectionStrings:MT:ConnectionString"];
  services.AddDbContext<MTContext>(options => options.UseSqlServer(MTConnection));
  ```

  ![16]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/16.png)

* 다음으로 .NET Core의 데이터베이스 CRUD 스캐폴딩을 진행합니다. 우선 **컨트롤러 폴더에 우측 클릭 - 추가 - 스캐폴드 항목 새로 만들기**를 클릭합니다.

  ![17]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/17.png)

* **MVC 종속성 추가** 에서 **Minimal Dependencies** 를 선택합니다.

  ![18]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/18.png)

* 생성 되어 열리는 **ScaffoldingReadMe.txt** 파일은 이미 프로젝트 템플릿에 포함된 내용이므로 추가로 작성할 내용이 없습니다. 다시 **컨트롤러 폴더 우측 클릭 - 추가 - 컨트롤러**를 선택합니다.

  ![19]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/19.png)

* 스캐폴드 추가 메뉴 중 Entity Framework를 사용하며 뷰가 포함된 MVC 컨트롤러를 추가합니다.

  ![20]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/20.png)

* 컨트롤러 추가 에서 모델 클래스는 Models/MT 하의 클래스를 데이터 컨텍스트 클래스는 Models/MT 하의 Context 클래스를 선택합니다.

  ![21]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/21.png)

  ![22]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/22.png)

* 스캐폴딩이 완료되면 각각의 테이블에 대한 컨트롤러와 CRUD 뷰페이지가 생성됩니다.

  ![23]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/23.png)

* 이전 단계까지 마무리 한 뒤, ASP.NET Core를 실행하여 확인합니다.

  ![24]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/24.png)

  ![25]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/25.png)

  ![27]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/27.png)

  ![28]({{ site.url }}/img/2017-08-11-connection-asp-dot-net-core-and-mssql-database/28.png)