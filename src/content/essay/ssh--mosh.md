---
{
  title: SSH & Mosh,
  date: 2026-06-17,
  tags: [ SSH ],
  draft: false,
  archive: true,
  slug: essay-260617-2lcx
}
---

SSH连接VPS输入延迟很明显，兜兜转转用回6神推荐的MobaXterm，早知道就直接用了，这个可以选择Mosh，除了低延迟网络环境和SSH拉不开差距，其他情况都是远超SSH，MobaXterm免费版足够用了。

这个mosh怎么说呢，难怪很多地方都没怎么提到，我目前使用起来遇到不少Bug，无论用哪款软件，都不如SSH稳定，而且闭源收费的SSH客户端（如Termius）光是SSH连接就能做到几乎无延迟，但是开启Mosh后会出现各类渲染问题，而且反应也没快多少，难怪编辑配置的时候默认disable。

目前一共用了这么几种方式使用SSH：
- Windows Terminal + PowerShell 7 + SSH
- Tabby + SSH
- MobaXterm + SSH/Mosh
- Termius + SSH/Mosh

最舒服的肯定是Termius，SSH下做到了几乎无感输入，其次是MobaXterm，Tabby跟Terminal差不了多少，只不过可以单独配置SSH，不像Terminal每次连接只能手打，但是这些除去原生Terminal都存在使用Bug，如果不是重度使用SSH，那么Terminal就足够了。



