---
layout: post
title: "Windows IIS 를 통한 asp.net core 웹앱 배포"
date: 2018-02-05 17:19 +0900
categories: [Development]
comments: true
---

* Windows 7 혹은 그 이상 Windows Server 2008 R2 혹은 그 이상의 OS가 필요합니다.
  1. (Windows 7기준) 제어판 - 프로그램 - 프로그램 및 기능에서 Windows 기능 사용/사용 안함을 선택
  2. 인터넷 정보 서비스(IIS)에 체크한 뒤 설치합니다.
* [.NET Core Windows Server Hosting](https://docs.microsoft.com/en-us/aspnet/core/publishing/iis)을 설치합니다.
* asp.net core 프로젝트의 Program.cs 파일에 UseIISIntegration() 함수를 확인합니다.

```c#
using System.IO;
using Microsoft.AspNetCore.Hosting;

namespace {ProjectName}
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

* IIS(인터넷 정보 서비스)관리자를 실행합니다.
  1. 사이트 - 웹 사이트 추가 클릭
  2. 사이트 이름, 실제 경로, 호스트 이름을 입력
  3. 응용 프로그램 풀 - 응용 프로그램 풀 추가 클릭
  4. .NET Framework 버전 = 관리 코드 없음, 파이프라인 모드 - 통합 으로 생성
  5. 위 웹사이트 기본 설정에서 응용 프로그램 풀을 위 응용프로그램 풀로 변경
* IIS에 설정한 실제 경로로 asp.net core 프로젝트를 게시 대상 위치(publish directory), 구성(release) 확인 후 게시합니다.