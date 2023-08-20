---
title: 關於我
---

<img src="https://s3-tpe-01.russel053.com/delia/delia_tech_hexo/avatar2.jpg" width=800>

C#後端工程師，畢業於屏東大學資訊管理系，2021年9月開始工程師之路，目前年資兩年，對於程式架構方面有很大的興趣，業餘時間會去各大社群看資深前輩們技術分享教學。

參與過電商系統翻新，負責核心訂單、購物車API開發，擅長電商金流、貨態、庫存變化...等領域知識，也參與過ERP系統流程規劃、微服務架構規劃、ERP後端API開發。

* 位置: Taipei City, Taiwan
* 電話: 0971080029
* 信箱: pingchun.hung@gmail.com
* 我的履歷: [CakeResume](https://www.cakeresume.com/pingchun.hung)
* GitHub: [Deliahung](https://github.com/DeliaHung)

---

# 技能清單
* 後端語言 & 框架
`C#` `ASP.NET Core` `ASP.NET Framwork` `WinFrom`
* SQL
`SQLServer` `MongoDB`
* ORM
`Entity Framwork` `Dapper` `ADO.NET`
* 前端
`HTML5` `CSS3` `jQuery` `Bootstrap` `Vue.js`
* 版本控制
`SVN` `Git`
* CI/CD
`Jenkins` `Bitbucket Pipeline`
---
# 工作經歷

## 無毒農(2022/9 ~ NOW)

### MediatR導入

將Controller、Service解偶，Api對應的UseCase獨立單獨Handler處理， 大幅`增加專案可讀性`、`可維護性`，同事都說讚。

>修改前

<img src="https://s3-tpe-01.russel053.com/delia/delia_tech_hexo/about/2023072402.png" width=600>

>修改後

```csharp
private readonly Isender _sender;

public class PersonController(ISender sender)
{
    _sender = sender;
}

[HttpGet]
public async Task<IActionResult> GetPersonPage(GetPersonPageQuery)
{
    return await _sender.send(GetPersonPageQuery)
}

[HttpGet]
public async Task<IActionResult> GetPersonById(GetPersonQuery)
{
    return await _sender.send(GetPersonQuery)
}

[HttpPost]
public async Task<IActionResult> CreatePerson(CreatePersonCommand)
{
    return await _sender.send(CreatePersonCommand)
}
```

<img src="https://s3-tpe-01.russel053.com/delia/delia_tech_hexo/about/2023072403.png" width=400>

### UnitOfWork導入

將每個Repossitory內的SaveChange抽離出來，外面包一層Unit Of Work，`減少建構子注入`、`劃分服務領域`、`Transation語法更直觀`。

<img src="https://s3-tpe-01.russel053.com/delia/delia_tech_hexo/about/2023072401.png" width=600>

### .NET Core 訊息微服務建置

使用.NET CAP套件，用KAFKA作為Event bus傳遞事件。
[本站文章連結](https://tech.deliahung.com/2023/07/08/Net-Core-CAP/)

>整體架構

<img src="https://s3-tpe-01.russel053.com/delia/delia_tech_hexo/about/CAP.png" width=600>

>寄送簡訊設計模式

```csharp
var setting = _SmsSetting.Filter(_ => _.Enable).OrderBy(_ => _.Sort).ToList();

foreach(var item in settings)
{
    var smsProvider = _smsFactory.GetSmsProvider(item.SmsProvierType);
    //紀錄log...
    var smsReponseDto = smsProvier.Send(smsRequestDto);
    //紀錄log...
    if (smsResponseDto.IsSuccess) break;
}
```

### 解決歷年週年慶搶購活動超賣問題

單機鎖lock語句、Redis鎖、樂觀鎖、悲觀鎖實作&分享

[本站文章連結](https://tech.deliahung.com/2023/06/21/EFCore-Concurrency/)

### UnitTest導入

使用`NUnit` with FluentAssertions & AutoFixture & NSubstitute。

### FluentValidation導入

`統一參數驗證方法`，搭配MediatR Pipeline統一處理Exception，並且`更好做單元測試`。

## 聯邦網通(2021/9 ~ 2022/9)

### 電商系統翻新
維持原本Database、後臺系統，將邏輯層改寫為API前後分離，了解許多電商領域知識。

### 訂單、購物車API
處理`折扣邏輯`、`購物車驗證`、`購物車分車邏輯`、`訂單狀態`、`庫存控制`。

### 金流串接
`聯邦串接`、`Line Pay金串接`

### 物流串接
`黑貓`

### 小工具API
banner、館別資訊...等存入快取`增加讀取速度`。

### 聯邦年節團購網站佈署維護
webform的老舊專案重新佈署。

### 聯邦紅利兌換網站佈署維護
webform的老舊專案重新佈署。

## 資策會C#工程師就業養成班 (2021/1 ~ 2021/8)

### 擔任專題技術長，負責小組畢業專題規劃，食譜&購物電商

### 專題導入三層式架構，IOC控制反轉，唯一有分層的組別

---

# 近期學習目標
- 持續練習OOP、設計模式
- 研究 DDD、Clean Architecture