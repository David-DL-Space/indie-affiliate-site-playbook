# indie-affiliate-site-playbook — Outline Draft
*From audiotest.io 0→revenue case study*

## 核心定位
一人公司 / AI-native builder 的细分工具站变现战术手册。从 idea 到首笔佣金的完整路径，基于 audiotest.io 实战抽象。

---

## 阶段 0：Idea Validation（48h 内验证 OR 放弃）
**目标：** 验证 idea 有市场需求 + 可变现 + 技术可行，避免浪费 2 周搭一个没人要的站。

### 验证清单
- [ ] **需求验证** — Google Trends + Reddit/HN/X 讨论热度（最近 6 个月 >100 mention？）
- [ ] **商业验证** — Amazon Associates 有没有对应品类（耳机/音响/DAC/声卡 etc）？单品佣金 >$2？
- [ ] **竞品成功案例分析** — 这个赛道有人赚到钱了吗？流量/变现模式是什么？（关键：找到成功先例）
- [ ] **竞品弱点验证** — SERP 前 10 都是谁？有没有弱点（老旧/慢/付费墙/UX 烂）？
- [ ] **SEO 验证** — 核心 query（如 "audio test"）月搜索量 >1k？难度 KD <40（Ahrefs/Semrush）？
- [ ] **技术验证** — 能不能纯前端实现（Web Audio API / Canvas / WebGL）？需要后端 API 吗？

### 竞品成功案例分析（Critical: 看到真金白银才有动力）

**为什么这一步重要？** 如果这个赛道没人赚到钱，你也很难赚到。找到 1-3 个成功先例，分析他们的流量来源、变现模式、弱点，给自己信心 + 找到差异化切入点。

#### 案例研究框架（以 audiotest.io 为例）

**竞品 1: OnlineTonesGenerator.com**
- **流量（SimilarWeb/Ahrefs）:** ~50k visits/month
- **变现模式:** Google Ads（页面顶部 + sidebar）
- **SEO 关键词:** "tone generator", "frequency generator"（排名 top 3）
- **弱点:** 
  - UI 老旧（2010 年代风格）
  - 广告多，UX 差
  - 没有 mobile 优化
  - 没有 affiliate（只有 ads）
- **机会:** 做一个现代、暗黑、无广告、affiliate 变现的版本 → audiotest.io

**竞品 2: AudioCheck.net**
- **流量:** ~80k visits/month
- **变现模式:** Affiliate（Amazon headphones/speakers）+ 少量 ads
- **SEO 关键词:** "speaker test", "audio test files"（排名 top 5）
- **弱点:**
  - 站点结构混乱（200+ 页面，没有清晰导航）
  - 测试文件是下载 WAV/MP3，不是 in-browser interactive
  - 没有 blog content（纯工具页，缺乏 buying guides）
- **机会:** 做 interactive browser tools + content hub + 更好的 affiliate integration

**竞品 3: Mimi Hearing Test (App)**
- **类型:** iOS/Android app（不是 web）
- **商业模式:** Freemium（免费测试 + $5.99/mo premium）
- **下载量:** 1M+ (Google Play)
- **弱点:**
  - 需要下载 app（摩擦高）
  - Web 版只是 landing page，不能直接用
- **机会:** 纯 web，0 下载，SEO 流量 > app store 流量

#### 如何挖掘竞品数据

1. **流量估算（免费工具）:**
   - SimilarWeb (前 5 结果免费看)
   - Ahrefs free tier（每天 1 次查询）
   - 或用 `browser` + 观察页面：广告多 = 流量大；Amazon affiliate links 多 = 在赚钱

2. **变现模式识别:**
   - 查看页面 source：Google AdSense code? Amazon affiliate tag?
   - 看 Privacy Policy：有 "Amazon Services LLC Associates Program" 字样 = 做 affiliate
   - 看 footer：Stripe/Gumroad 链接 = 有付费产品

3. **SEO 关键词反查（免费）:**
   - Ahrefs free "Top Pages" report
   - 或 Google `site:competitor.com` 手动看 indexed pages
   - 或 `curl competitor.com/sitemap.xml | grep '<loc>'` 看他们的页面结构

4. **弱点识别 checklist:**
   - [ ] Lighthouse score <70？
   - [ ] Mobile 上 UX 烂？
   - [ ] 广告太多？
   - [ ] 没有 blog/content？
   - [ ] 最后更新时间 >2 年？
   - [ ] 没有 HTTPS？
   - [ ] 没有国际化（只有英文）？

#### 成功案例的"刺激阈值"

你需要找到至少 **1 个月流量 >10k 或月收入 >$500 的竞品**，才算验证了这个赛道有钱赚。

- 如果竞品月收入 <$100 → 赛道太小，pivot
- 如果竞品月收入 $500-5k → 可以做，solo builder 够吃
- 如果竞品月收入 >$10k → 大赛道，但竞争激烈，需要找差异化切入点

### 工具
- Google Trends, Reddit search, X search (`xitter` skill), HN Algolia
- SimilarWeb, Ahrefs free tier, SEMrush free trial
- Amazon Associates product search (浏览器 + Playwright if login needed)
- Can I Use (Web API 兼容性检查)

### 决策门
48h 内拿到以下 3 个 YES：
1. **找到 1 个成功先例**（月流量 >10k 或月收入 >$500）
2. **核心 query 月搜 >1k + 前 10 有可击败对手**（老旧/慢/UX 差）
3. **技术路径清晰 + 变现路径清晰**（Amazon 品类存在 + 单品佣金 >$2）

**通过 → 进入阶段 1 | 不通过 → pivot 或放弃**

---

## 阶段 1：Tech Stack（选型 + boilerplate，1 天）
**目标：** 最小可行技术栈，dev→prod 路径清晰，0 运营成本（或 <$10/mo）。

### audiotest.io 实战选型
| 层 | 选择 | 为什么 |
|---|---|---|
| 框架 | Next.js 15 (App Router) | SEO 友好（SSG）、Vercel 一键部署、React 生态 |
| 样式 | Tailwind CSS | 快速迭代、暗黑主题开箱即用 |
| 音频 | Web Audio API (原生) | 0 依赖、纯前端、性能好 |
| 国际化 | next-intl | App Router 原生支持、路由自动 /zh 前缀 |
| Analytics | GA4 + @next/third-parties/google | 免费、custom event 支持 |
| 部署 | Vercel Hobby (免费) | 自动 CI/CD、preview deploy、edge 全球加速 |
| 域名 | GoDaddy + Cloudflare DNS | 便宜、API 可编程 |
| 联盟 | Amazon Associates | 最大联盟平台、佣金结构透明 |

### Boilerplate checklist
- [ ] `pnpm create next-app` → App Router + Tailwind + TypeScript
- [ ] 暗黑主题 baseline（`dark` class + Tailwind config）
- [ ] 国际化 scaffold（`/[locale]/layout.tsx`，EN + ZH）
- [ ] GA4 event 基础封装（`lib/gtag.ts`）
- [ ] Git repo + GitHub + Vercel 连接
- [ ] Custom domain DNS CNAME → Vercel
- [ ] Favicon + OG image 占位符

### 参考 skills
- `vercel-deploy` — Vercel 部署 + 域名绑定 pitfalls
- `nextjs-seo` — Next.js App Router SEO 优化清单
- `godaddy-dns` — GoDaddy API 配置 DNS

---

## 阶段 2：MVP Build（核心功能 v0.1，3-5 天）
**目标：** 上线一个**可用**的工具（哪怕只有 1 个功能），快速拿到真实用户反馈。

### audiotest.io v0.1 scope
- ✅ **Homepage = 核心工具** — Stereo L/R channel test（点击播放左右声道）
- ✅ **2-3 个辅助工具** — Tone generator, Frequency sweep（复用 Web Audio API）
- ✅ **极简 UI** — 单页，暗黑风，Noto Sans SC 中文字体
- ✅ **基础 SEO** — `<title>`, `<meta description>`, OG tags, sitemap.xml
- ❌ **暂不做** — Blog, 产品卡片, FAQ, 复杂动画

### 开发顺序（TDD 思路）
1. **Audio engine 先行** — 写纯 TS 的 Web Audio 逻辑（oscillator, gain, panner），浏览器 console 测试
2. **UI 组件封装** — `<AudioTestCard>`, `<ToneGenerator>` 等，Storybook or 独立页面调试
3. **集成 + 路由** — 组装到 Next.js 页面，`/`, `/tone-generator`, `/frequency-sweep`
4. **国际化** — 抽 strings 到 `messages/en.json`, `messages/zh.json`
5. **Metadata** — 每个页面的 `generateMetadata()` (App Router)
6. **Sitemap** — `app/sitemap.ts` 动态生成（含 hreflang alternates）

### 验证 gate
- [ ] 每个工具都能在 Chrome + Safari + Firefox 上正常运行（iOS Safari 是坑，需 user gesture 才能 play）
- [ ] Lighthouse Score >90（Performance, Accessibility, SEO）
- [ ] `curl -I https://audiotest.io` 返回 200
- [ ] Google Search Console 提交 sitemap（虽然不会立刻索引）

---

## 阶段 3：SEO Foundation（技术 SEO，2 天）
**目标：** 打好 SEO 地基，让 Google 能爬、能索引、能理解你的页面。

### Technical SEO checklist
- [ ] **Sitemap.xml** — 所有页面 + hreflang alternates（EN ↔ ZH）
- [ ] **Robots.txt** — 允许爬虫，指向 sitemap
- [ ] **Schema.org markup** — WebSite, WebPage, BreadcrumbList（JSON-LD）
- [ ] **OG tags + Twitter Card** — 每个页面独立 title/description/image
- [ ] **Canonical URLs** — 避免 /zh 和 / 重复内容
- [ ] **Mobile-friendly** — Viewport meta, 响应式布局
- [ ] **Page speed** — 图片优化（Next.js Image），code splitting，CDN
- [ ] **IndexNow** — Bing/Yandex 快速索引（可选，Vercel Edge Function 触发）

### Google Search Console setup
1. 添加站点（DNS TXT 验证 or Vercel auto-verify）
2. 提交 sitemap: `https://audiotest.io/sitemap.xml`
3. 提交 homepage + 2-3 核心工具页的 URL（手动 Request Indexing）

### 参考 skills
- `nextjs-seo` — App Router SEO 最佳实践
- `affiliate-growth-analytics` > `references/ga4-nextjs-setup.md` — Schema 模板

---

## 阶段 4：Content Strategy（3 层内容模型，持续）
**目标：** 工具页流量低购买意图 → 用 blog 捕获高购买意图 query → 内链漏斗转化。

### 3-layer content model
```
L1: Tool pages (现有)          — "test / check" intent → 低购买意图，但 SEO 入口
L2: Buying guides (高 ROI)     — "best / review" intent → 高购买意图
L3: How-to / troubleshooting   — "how to / fix" intent → 中购买意图
L4: Brand comparisons          — "X vs Y" intent → 最高购买意图（需站点权威）
```

### Content 优先级（audiotest.io 实战）
1. **L3 first** — 直接关联现有工具，最低 effort，最快索引
   - "How to test headphone left right channel" → 内链到 `/` stereo test
   - "How to find tinnitus frequency" → 内链到 `/tinnitus-test`
2. **L2 second** — 最高 revenue potential，但需 1-2 个月 rank
   - "Best budget headphones for mixing 2026"
   - "Best studio monitors under $300"
3. **L4 third** — 需要站点 DR >20 才有戏
   - "Audio-Technica ATH-M50X vs Sony MDR-7506"

---

### 长尾词战术：小词聚合成大流量（Critical: niche site 的核心生存策略）

**核心理念：** 不要只盯着 "audio test" (10k/mo, KD 60) 这种大词。挖 100 个月搜 50-500 的长尾词，每个排到 top 3，聚合起来流量 > 1 个大词排第 5。

#### 长尾词挖掘 4 步法

**Step 1: 从工具页反推用户场景**

每个工具页 = 1 个核心用户任务。把任务拆成 **细分场景 + 问题**，每个场景 = 1 个长尾词机会。

**示例：Stereo L/R Test 工具页**

| 用户场景 | 问题 | 长尾 keyword (月搜 50-500) | Content angle |
|---|---|---|---|
| 新买耳机到手 | 怎么测左右声道？ | "how to test left right headphone channel" | How-to (L3) |
| 一边声音小 | 为什么一边耳机声音小？ | "one headphone quieter than other" | Troubleshooting (L3) |
| 修电脑后 | 电脑音频设置错了？ | "stereo audio test windows 11" | OS-specific (L3) |
| 买二手耳机 | 二手耳机怎么检查坏没坏？ | "how to check used headphones before buying" | Buying guide (L2) |
| DAC 调试 | DAC 左右平衡调对了吗？ | "dac balance test" | Niche tech (L3) |

**每 1 个工具页 → 至少 5-10 个长尾词机会。** 6 个工具页 = 30-60 篇 blog 的 seed list。

---

**Step 2: GSC "People Also Ask" 和实际搜索挖掘**

工具页上线 2-4 周后，GSC 会显示**你没想到的 query**（用户真实搜索）。这些是最精准的长尾词来源。

**audiotest.io GSC 实战数据（2026-06-12）：**

| Query | Impressions | Position | 你的现有页面 | 长尾词机会 |
|---|---|---|---|---|
| "audio test online" | 2 | 54.5 | `/` (homepage) | ✅ "best free online audio test tools" (L2 buying guide) |
| "audiotest" | 5 | 29.0 | `/` | ❌ 品牌词，已覆盖 |
| "test loa online" | 1 | 80.0 | `/` | ✅ "speaker test online free" (L3 + L2) |
| "audio tester online" | 2 | 65.5 | `/` | ✅ "audio equipment tester" (L2 工具推荐) |

**GSC 挖掘 SOP:**
1. GSC → Performance → Queries，筛选 `Impressions > 1` 且 `Position > 10`
2. 找到 position 11-50 的 query（有曝光但没点击 = 机会）
3. 每个 query 问：**有没有更具体的变体？** 
   - "audio test online" → "audio test online no download" / "audio test online for headphones" / "audio test online bass"
4. Google 这些变体，看 PAA (People Also Ask) 框，每个 PAA = 1 个长尾词

---

**Step 3: AlsoAsked / AnswerThePublic 扩展**

免费工具，输入核心 query，自动生成 50-200 个问题变体。

**示例：输入 "headphone test"**

AlsoAsked 输出（树状图）：
```
headphone test
├─ how to test headphones
│  ├─ how to test headphones for damage
│  ├─ how to test headphones on pc
│  └─ how to test headphones with multimeter
├─ what is headphone test
│  ├─ what is the best headphone test
│  └─ what frequency should I test my headphones
├─ where to test headphones
│  ├─ where to test headphones in store
│  └─ where to test headphones before buying
└─ why test headphones
    ├─ why do headphones need burn in
    └─ why my headphones sound muffled
```

每个分支 = 1 个长尾词 + 1 个 user intent。你现在有 **20+ 篇 blog 的题目清单**，每篇 500-1000 字，1-2 天写完。

---

**Step 4: 竞品 sitemap 反查（偷竞品的长尾词）**

竞品排名好的页面 = 验证过的长尾词。直接抄作业。

```bash
# 拉竞品 sitemap
curl -s https://audiocheck.net/sitemap.xml | grep -oP '(?<=<loc>)[^<]+' | head -50

# 输出示例：
# https://audiocheck.net/audiotests_left_right.php
# https://audiocheck.net/audiotests_frequencycheckhigh.php
# https://audiocheck.net/audiotests_subwooferkicktest.php
# https://audiocheck.net/download.php
```

**每个 URL = 1 个目标 keyword。** 把 URL slug 翻译成英文 query：
- `audiotests_left_right.php` → "left right audio test"
- `frequencycheckhigh` → "high frequency hearing test"
- `subwooferkicktest` → "subwoofer bass test"

然后你做**更好的版本**（interactive, 暗黑 UI, blog content, affiliate integration）。

---

### 长尾词聚合的数学：小词如何变成大流量

**场景：** 你想排 "audio test" (10k/mo, KD 60)，但你是新站，DR 0，排不上。

**长尾策略：**
- 挖 50 个月搜 100-300 的长尾词（如 "stereo test online", "audio test no download", "headphone channel test", "speaker phase test" etc）
- 每个词写 1 篇 800 字 blog，2 周写完
- 长尾词 KD 通常 <20，新站也能排 top 3
- 假设每个词排 top 3 → CTR 10% → 每词带来 10-30 visits/mo
- 50 个词 × 20 visits = **1000 visits/mo**，超过 "audio test" 排第 10 的流量（~500 visits/mo）

**更重要的是：** 长尾词的**购买意图更高**。

- "audio test" → 泛需求，可能是学生做作业
- "best headphones for audio testing under $100" → 明确购买意图，affiliate CTR 高 3-5 倍

**长尾词内容的 4 个黄金法则：**

1. **Volume 小但 aggregated volume 大** — 50 个月搜 100 的词 = 5000/mo total
2. **KD 低，新站也能排** — 长尾词竞争少，2-4 周就能进 top 3
3. **Intent 精准，转化率高** — 用户搜得越具体，越接近购买决策
4. **内链权重传导** — 50 篇 blog 都内链到你的工具页 → 工具页的 DA/DR 提升 → 大词也开始 rank

---

### Niche 场景挖掘：找到"被忽略的细分用户"

主流竞品通常只做**通用场景**。找到 3-5 个**被忽略的细分场景**，做深度内容，monopolize 这些长尾词。

**audiotest.io 实战：5 个 niche 场景**

| Niche 场景 | 被忽略原因 | 目标用户 | 关键词集群 (5-10 词/场景) | Content 策略 |
|---|---|---|---|---|
| **Home theater setup** | 竞品只做耳机，不做音响 | DIY 家庭影院玩家 | "surround sound test", "5.1 speaker test", "subwoofer phase test" | L3 how-to + L2 speaker 推荐 |
| **Car audio tuning** | 竞品没有车载场景 | 汽车音响改装 | "car speaker test", "car subwoofer test frequency", "car audio left right balance" | L3 + L2 car audio gear |
| **Podcast/streaming mic check** | 竞品是 audiophile 向，不是 creator 向 | 播客/主播 | "mic test for streaming", "how to test usb mic", "xlr mic test setup" | L3 + L2 podcast mic 推荐 |
| **Hearing loss self-test** | 医疗敏感，竞品不敢碰 | 40+ 岁用户 | "online hearing test frequency", "can I test my hearing at home", "tinnitus frequency finder" | L3 + disclaimer (not medical advice) |
| **Gaming headset troubleshoot** | 游戏玩家场景，竞品没针对性 | PC/console 玩家 | "gaming headset left ear not working", "surround sound test for gaming", "how to test gaming headset mic" | L3 troubleshooting + L2 gaming headset |

**每个 niche 场景 = 5-10 篇 blog = 500-2000 visits/mo**。5 个场景 = 2500-10000 visits/mo，且这些用户**没有其他好的选择**（你 monopolize 这个 niche）。

---

### 长尾词 content 生产 SOP (AI-native workflow)

1. **Batch keyword research** (1 天)
   - GSC actual queries + AlsoAsked + 竞品 sitemap → 50-100 个长尾词 list
   - 筛选：月搜 >50, KD <30, intent match (how-to / best / vs / troubleshooting)

2. **Competitive SERP analysis** (用 `browser` + `browser_console` 批量抓)
   - 每个 keyword Google 前 5 结果
   - 抓 title, H1, H2, word count, 内链数
   - 找到 **common H2 pattern** (如 "how to test" 类都有 "What you need" / "Step by step" / "Troubleshooting" 三段)

3. **AI outline generation** (Claude/GPT)
   - 输入：keyword + SERP analysis + 你的工具页 URL
   - 输出：800-1500 字 outline，含 FAQ

4. **Draft + Humanize**
   - Claude 写初稿
   - `humanizer` skill 去 AI 腔
   - 人工 review：插入 1-2 个 personal anecdote，加 inline product cards

5. **Schema + Internal links**
   - Article schema (published date, author, image)
   - FAQ schema (从 PAA 来)
   - 内链：每篇至少 2 个内链到工具页 + 1 个内链到 related blog

6. **Publish + GSC submit**
   - `git push origin master`
   - Vercel auto-deploy
   - GSC Request Indexing（手动，每天最多 10 个 URL）

7. **2 周后 monitor**
   - GSC 看 impressions + position
   - 如果 position >20，加 1-2 个 backlinks 到这篇 blog
   - 如果 position 10-20，加 300 字 depth + 1 个 FAQ

**Throughput:** 1 人 + AI，每天 2-3 篇长尾词 blog（质量 > 数量，别做 AI spam）。

### Content 生产流程（AI-native）
1. **Keyword research** — GSC actual queries + Ahrefs/AlsoAsked
2. **Competitive SERP analysis** — 前 5 名的 title/H1/H2/word count/内链（`browser` + `browser_console`）
3. **Outline generation** — Claude/GPT 生成大纲 + FAQ
4. **Draft + humanize** — 初稿 → `humanizer` skill 去 AI 味 → 人工 review
5. **Product matching** — 每个 section 插入 contextual affiliate cards（不是 sidebar spam）
6. **Schema markup** — Article/HowTo/FAQPage JSON-LD
7. **Publish + GSC submit** — `git push origin master` → Vercel auto-deploy → GSC Request Indexing

### 参考 skills
- `affiliate-growth-analytics` > Content strategy section
- `humanizer` — 去 AI 腔调

---

## 阶段 5：Affiliate Integration（产品卡片 + 事件追踪，2 天）
**目标：** 把流量转化成点击 → 订单 → 佣金。追踪每一步漏斗。

### Amazon Associates setup
1. 注册 Amazon Associates（需要一个已上线的站 + 真实流量，冷启动悖论）
2. 拿到 affiliate tag: `audiotest-20` (US) / `audiotest-21` (UK)
3. 产品选品策略：
   - **Budget tier** ($20-50) — 高转化，低佣金（~$1-2）
   - **Mid tier** ($100-300) — 平衡
   - **Premium tier** ($500+) — 低转化，高佣金（$20-50）
   - **Accessories** (线材/支架/耳塞) — 冲动消费，高转化

### Affiliate card 实现（Next.js）
```tsx
// components/AffiliateCard.tsx
import productsData from "@/data/products-live.json";

export function AffiliateCard({ asin, position, page }) {
  const product = productsData.products[asin];
  const affiliateUrl = `https://www.amazon.com/dp/${asin}?tag=audiotest-20`;

  // Fire impression event on mount (once per product per page load)
  useEffect(() => {
    if (window.gtag && !impressionFired.current) {
      window.gtag("event", "affiliate_impression", {
        product_name: product.title,
        product_tier: product.tier, // budget/mid/premium
        product_price: product.price,
        page, position, locale: "en",
      });
      impressionFired.current = true;
    }
  }, []);

  const handleClick = () => {
    if (window.gtag) {
      window.gtag("event", "affiliate_click", {
        product_name: product.title,
        product_tier: product.tier,
        page, position, locale: "en",
        link_url: affiliateUrl,
      });
    }
  };

  return (
    <a href={affiliateUrl} target="_blank" rel="nofollow noopener sponsored"
       onClick={handleClick} className="...">
      <img src={product.localImage} />
      <span>{product.title}</span>
      <span>{product.price}</span>
    </a>
  );
}
```

### GA4 custom events (MUST register as custom dimensions in GA4 Admin)
- `affiliate_impression` — product rendered on screen
- `affiliate_click` — user clicked affiliate link

### 漏斗追踪公式
```
Visitors → Tool Users → Impressions → Clicks → Orders (Amazon) → Revenue
  ↑ GA4      ↑ GA4         ↑ custom       ↑ custom   ↑ Amazon      ↑ Amazon
```

### 参考 skills
- `affiliate-growth-analytics` — 完整事件追踪实现 + troubleshoot-scenario product matching pattern
- `affiliate-product-cards` — Next.js affiliate card 实现

---

## 阶段 6：Analytics & Reporting（数据闭环，1 天 setup + 持续优化）
**目标：** 知道哪些页面/产品/渠道在赚钱，哪些在浪费流量。

### Data sources
| Source | What it tells you | API |
|---|---|---|
| **GA4** | 流量、漏斗、事件 | Google Analytics Data API v1beta |
| **GSC** | 关键词排名、CTR、曝光 | Search Console API |
| **Amazon Associates** | 点击、订单、佣金 | 无 API — Playwright scrape |
| **Vercel Analytics** | 真实访客数（fallback） | Vercel API |

### Daily report structure（自动化 cron）
```
📊 audiotest.io Daily — YYYY-MM-DD

TRAFFIC
- Visitors, pageviews, bounce (vs yesterday, vs 7d avg)
- Top pages + sources

FUNNEL
- Visitors → Impressions → Clicks
- Top products by CTR

REVENUE (Amazon — 24-48h delay)
- Clicks / Orders / Revenue
- Top earners

SEO (GSC — 3d delay)
- Top keywords (position, trend)
- Dropped keywords ⚠️
- Opportunity keywords (high impr, rank >10)

ACTIONS
- 🟢 Quick wins
- 🟡 This week
- 🔵 Monitor
```

### Visual report delivery (preferred)
HTML dashboard → Playwright `--full-page` screenshot → `MEDIA:<png>` 发到 Feishu/WeChat

### 参考 skills
- `affiliate-growth-analytics` — 完整 GA4 + GSC + Associates 数据管道
- `affiliate-growth-analytics` > `references/visual-report-design.md` — 暗黑风格 HTML 模板

---

## 阶段 7：Growth — Backlinks（从 0→50 backlinks，持续 3-6 个月）
**目标：** Google 看 backlinks 判断站点权威。0 backlinks = 排名卡在 page 3-8；10+ backlinks = 进 page 1-2。

### Backlink 策略（3 tracks 并行）
#### Track 1: GitHub awesome-lists (最快，1-2 周见效)
- 搜 `awesome-audio`, `awesome-web-audio`, `awesome-no-login-web-apps`, `awesome-self-hosted`
- Fork → branch → 在相关 section 加一行 → PR
- **Merge rate checklist:**
  - 最近 30 个 closed PR 中 >50% merged？
  - 最近 6 个月有 commit？
  - README 有 Contributing guidelines？
- audiotest.io 实战：2 个 PR 提交（awesome-webaudio, awesome-no-login-web-apps）

#### Track 2: Niche indie blogs (中等难度，2-4 周)
- **目标画像:** DR 20-50 的独立 audiophile/音频测评博客，已经 link 出去给其他 free tools
- **发现渠道:** 
  - Google `"audio test" OR "sound test" + "free tools" + blog`
  - Reddit r/audiophile sidebar
  - 竞品的 backlink profile（Ahrefs "Backlinks" tab）
- **Outreach 路径（3 tier）:**
  - **Tier 1 (highest conversion):** 已有 /tools 或 /resources 页 → 邮件请求添加
  - **Tier 2 (guest post):** 提 pitch："5 free browser tools every [audience] uses"
  - **Tier 3 (editorial mention):** 评论最近帖子 + contextual 提及你的工具

- **Email template structure:**
  ```
  Subject: Free [tool type] — fit for your [resources page]?
  
  Hi [Name],
  [1 sentence: 我读你的 X 文章，很有用]
  [1 sentence: 我做了 Y 工具，解决 Z 问题]
  [1 sentence: 可能适合你的 [resources page / 读者]]
  
  [Tool URL]
  [1-line description]
  [GitHub source if open-source]
  
  [Ask: 加到 resources page? 或者 guest post?]
  
  Best,
  [Your name]
  ```

- audiotest.io 实战：12 个 niche blog targets 挖掘 → 5 个 Tier 1 邮件草稿
  - DIY Audio Heaven, Archimago, Well-Tempered Computer, Audiophilia, HiFi Knights

#### Track 3: Reddit/HN/Forums (免费但低 SEO 价值)
- Reddit: r/audiophile, r/headphones, r/hometheater (self-promo 限制严格，只在 "weekly recommend" thread 提及)
- HN Show HN: 标题 "Show HN: Free in-browser audio test toolkit" + 说明 tech stack
- Forums: Head-Fi, AVS Forum, Gearslutz (需要真实参与讨论，不能裸发链接)

### Backlink tracking (Linear issues)
每个 outreach target = 1 个 Linear issue，status flow:
```
pending → sent → replied → linked ✅
```

只有真实 DoFollow 链接上线后才标 Done。

### 参考 skills
- `github-pr-workflow` — GitHub PR 最佳实践
- 本次实战 subagent research deliverable — 12 niche blog targets 详细分析

---

## 阶段 8：Optimization & Scale（数据驱动迭代，ongoing）
**目标：** 从数据找瓶颈 → 针对性优化 → 复利增长。

### 优化方向（按 ROI 排序）
1. **Top landing pages 的 bounce rate 过高？**
   - 加内链到其他工具
   - 加 "Related tools" section
   - Improve CTA clarity

2. **某个 product 曝光高但 CTR 低？**
   - 换图（Amazon 允许 7 天内的 product image cache）
   - 改描述
   - 调整 position（把高 CTR 产品放前面）

3. **某个 keyword 排名卡在 11-20？**
   - 加 1-2 个 backlinks 针对这个页面
   - 增加 content depth（现在 500 字 → 1500 字）
   - 加 FAQ schema

4. **Affiliate clicks 高但 conversion 低？**
   - 产品选品问题（price too high / 品类不匹配）
   - 或者正常（Amazon 平均 conversion 3-8%）

5. **流量来了但 affiliate impression 很少？**
   - Sidebar 被忽略 → 改成 inline contextual cards
   - 或者 CSS `hidden` 导致多次 mount → 修复 useSyncExternalStore pattern

### A/B test ideas (Vercel Edge Config + Middleware)
- Affiliate card placement: sidebar vs inline
- Product mix: 3 budget vs 2 budget + 1 premium
- CTA wording: "View on Amazon" vs "Check Price"

### Scale 策略（当月收入 >$100 后）
- **内容 SEO:** 每周 1-2 篇 blog（L2 buying guides）
- **工具扩展:** 加新工具页（如 audiotest.io 加 `/microphone-test`, `/speaker-test`）
- **多语言:** 加 JP/DE/FR（大市场 + Amazon Associates 支持）
- **Backlinks:** 持续 outreach，目标 50+ backlinks in 6 months

---

## Tools & Skills 总清单

### Essential skills (本 playbook 依赖)
- `vercel-deploy` — Vercel 部署
- `nextjs-seo` — Next.js SEO 优化
- `affiliate-growth-analytics` — 联盟营销数据管道
- `affiliate-product-cards` — 产品卡片实现
- `github-pr-workflow` — GitHub PR 流程
- `godaddy-dns` — DNS 管理
- `linear` — 任务跟踪
- `humanizer` — 去 AI 腔调

### Optional enhancements
- `replicate-api` — AI 生成 social media poster
- `sketch` — 快速 UI mockup
- `systemmatic-debugging` — 遇到坑时的 debug 流程
- `obsidian` — 知识库沉淀

---

## Success Metrics（分阶段 milestone）

### Month 1 (MVP → First Traffic)
- [ ] 站点上线，Lighthouse >90
- [ ] GSC 收录 >5 个页面
- [ ] GA4 显示 >10 unique visitors
- [ ] 2-3 个 awesome-list backlinks merged

### Month 2 (SEO → First Clicks)
- [ ] GSC 显示 >50 impressions/day
- [ ] 某个核心 keyword 进 page 2 (rank 11-20)
- [ ] GA4 affiliate_click >10 events
- [ ] 5+ niche blog backlinks

### Month 3 (Clicks → First Revenue)
- [ ] Amazon Associates account approved
- [ ] First order confirmed (可能佣金只有 $0.5，但是 PMF 验证)
- [ ] 某个 keyword 进 page 1 (rank 1-10)
- [ ] Organic traffic >100 sessions/day

### Month 6 (Scale)
- [ ] Monthly revenue >$100
- [ ] 10+ keywords in top 10
- [ ] 50+ backlinks (Ahrefs DR >15)
- [ ] Content hub >20 blog posts

---

## Pitfalls（audiotest.io 踩过的坑）

### SEO
- **GSC 3-day delay** — 别指望今天发的文章明天就有排名数据
- **Sitemap submission 需要 write scope** — OAuth 只有 `webmasters.readonly` 会 403
- **Hreflang alternates 必须双向** — EN 指向 ZH 的同时，ZH 也要指回 EN

### Affiliate
- **Impression inflation (2x)** — CSS `hidden` 的 mobile/desktop 两个实例都会 mount，用 `useSyncExternalStore` + conditional render
- **Amazon Associates 冷启动** — 新站无流量无法申请 → 先用 GA4 event proxy 估算，等有 50+ sessions/day 再申请

### Analytics
- **GA4 bounce rate 是 0.0-1.0 fraction** — 显示时要 ×100
- **Hermes config.yaml folded scalars** — 别用 `line.split(': ')` parse，用 `yaml.safe_load()`
- **Associates scraper session 过期** — Playwright 需要 two-pass OTP 流程，state 存 `~/.hermes/cache/amazon_state.json`

### Deployment
- **Vercel Hobby git author 限制** — `vercel deploy` CLI 会被 reject，只能 `git push` 触发 auto-deploy
- **Cloudflare proxy 缓存坑** — DNS 的 orange cloud 图标 = proxy，会 cache static assets，开发时关掉

---

## Next Steps（用这个 playbook 干什么）

1. **Copy as template** — 下次做新 niche site 时（如 "color blindness test" / "typing speed test" / "wifi analyzer"），直接走这 8 阶段
2. **Extract reusable code** — 把 affiliate card / GA4 tracking / sitemap generation 抽成 npm package or GitHub template
3. **Document decision tree** — 什么时候该 pivot？什么时候该 scale？什么时候该卖站？
4. **Build in public** — 把这个 playbook 本身做成一个 SEO content（"How I built a $XXX/mo affiliate site in 90 days"）

---

---

## When to Pivot: 决策树（何时放弃/调整/加倍投入）

**核心原则：** 数据驱动决策，别因为 sunk cost 继续浪费时间。每个阶段都有明确的"放弃信号"和"加倍信号"。

### Month 1 决策点：有没有 traction？

| 指标 | 健康值 | 警戒值 | 决策 |
|---|---|---|---|
| GSC indexed pages | >5 | <3 | <3 = sitemap/robots 有问题，修复后再等 2 周 |
| GSC impressions/day | >10 | <5 | <5 = SEO 基础没打好，回阶段 3 |
| GA4 unique visitors | >10 | <5 | <5 且都是你自己 = 没人关心这个工具，考虑 pivot |
| Awesome-list backlinks | >1 merged | 0 PR merged | 0 = PR 质量问题 or 选错 list，重新选 |

**Month 1 决策：**
- ✅ **所有指标达标 → 继续阶段 4-5（内容 + affiliate）**
- ⚠️ **1-2 个指标不达标 → 诊断 + 修复，再等 2 周**
- ❌ **3+ 指标不达标 → Pivot or 放弃**
  - Pivot 方向：换一个相关但更 niche 的工具（如从 "audio test" pivot 到 "tinnitus frequency finder"）
  - 或放弃：承认这个 idea 没市场，启动下一个 idea（你只损失了 1 个月 + $10 域名）

---

### Month 2 决策点：有没有 organic traffic 增长？

| 指标 | 健康值 | 警戒值 | 决策 |
|---|---|---|---|
| GSC impressions/day | >50 | <20 | <20 = 内容不够 or backlinks 太少 |
| 至少 1 个 keyword 进 page 2 | Yes (rank 11-20) | No (all >20) | No = SEO 难度太高 or 站点权威不够 |
| GA4 sessions/day | >20 | <10 | <10 = 即使有 impressions 也没点击，title/description 不吸引 |
| Affiliate clicks (GA4 event) | >5 | 0 | 0 = 产品选品问题 or 产品卡片 UI 问题 |

**Month 2 决策：**
- ✅ **健康值 → 加倍投入内容 + backlinks（阶段 7）**
- ⚠️ **警戒值 → 诊断瓶颈：**
  - Impressions 低 → 加 10-20 篇长尾词 blog
  - Rank 差 → 每周 2-3 个 niche blog backlinks
  - CTR 低 → 重写 title/description（A/B test）
  - Affiliate clicks 0 → 换产品 or 改 placement（sidebar → inline）
- ❌ **如果加了 20 篇 blog + 5 个 backlinks 后，impressions 还是 <20/day → 赛道太小或竞争太激烈，考虑 pivot**

---

### Month 3 决策点：有没有首笔收入？

| 指标 | 健康值 | 警戒值 | 决策 |
|---|---|---|---|
| Amazon Associates approved | Yes | Application rejected | Rejected = 流量太假（自己刷的）or 站点质量问题 |
| First affiliate order | ≥1 order | 0 orders | 0 = CTR 问题 or 产品选品问题 |
| Organic sessions/day | >50 | <30 | <30 = SEO 增长停滞 |
| At least 1 keyword in top 10 | Yes | No | No = backlinks 不够 or 内容质量问题 |

**Month 3 决策：**
- ✅ **First order (哪怕 $0.5 佣金) = PMF 验证，Scale 阶段开始（阶段 8）**
  - 加倍内容产出（每周 3-5 篇）
  - 加倍 backlink outreach（每周 5-10 封邮件）
  - 考虑多语言（JP/DE/FR）
- ⚠️ **0 orders 但 clicks >20 → Amazon conversion 问题（正常 3-8%），继续观察 2 周**
- ⚠️ **0 clicks 但 sessions >50 → 产品 placement 问题，做 A/B test（sidebar vs inline）**
- ❌ **Sessions <30 且无增长趋势 → SEO 天花板，两个选择：**
  1. **Pivot 到付费流量**（Google Ads / Reddit Ads）— 需要更高客单价产品（>$100）才能 ROI 正
  2. **放弃此项目**，总结教训（哪里卡住了？SEO 难度估错？内容质量不够？Backlinks 太少？），启动下一个 idea

---

### Month 6 决策点：能不能 scale 到 $500/mo？

| 指标 | 健康值 (scale) | 平台期 | 决策 |
|---|---|---|---|
| Monthly revenue | >$500 | $100-200 | $100-200 = 可持续但不够 quit job，决定要不要继续投入 |
| Organic sessions/day | >200 | 50-100 | 50-100 = SEO 增长放缓，需要更多 backlinks or 新内容 pillar |
| Backlinks (Ahrefs) | >50 | 10-20 | 10-20 = 增长瓶颈，backlink outreach 不够 aggressive |
| Blog posts | >50 | 20-30 | 20-30 = 内容覆盖不够，继续挖长尾词 |

**Month 6 决策：**
- ✅ **Revenue >$500/mo → 这是一个成功的 side project，两条路：**
  1. **继续 scale**（目标 $2k/mo）— 多语言 + 更多工具页 + 付费 backlinks (HARO / guest posts)
  2. **Sell the site**（Flippa / Empire Flippers）— 通常 24-36x 月收入（$500/mo = $12-18k 售价）
- ⚠️ **Revenue $100-200/mo → 平台期，选择：**
  - **加倍投入**（每天 2-3 小时，持续 3 个月）看能否突破 $500
  - **维护模式**（每周 1-2 篇 blog）保持现状，启动第 2 个 niche site
- ❌ **Revenue <$100/mo 且 6 个月无增长 → 放弃或卖掉（$1-3k）**
  - 总结教训文档（什么有效？什么无效？）
  - 下一个 idea 避免同样错误

---

### Pivot vs 放弃的决策矩阵

|  | 流量增长 ↑ | 流量平台期 → | 流量下降 ↓ |
|---|---|---|---|
| **有收入** (>$50/mo) | ✅ Scale | ⚠️ 维护 or 卖 | ⚠️ 诊断（算法更新？竞品超车？） |
| **无收入 + 有 clicks** | ⚠️ 观察 2 周（Amazon conversion 需要时间） | ⚠️ Pivot 产品选品 | ❌ 放弃 or 卖 |
| **无 clicks** | ⚠️ 改 affiliate placement | ❌ Pivot or 放弃 | ❌ 放弃 |

---

## Meta: 这个 playbook 本身的定位

- **读者:** AI-native indie builders, 一人公司, side project hustlers
- **前置知识:** 会写代码（Next.js / React），懂基础 SEO 概念，有 Hermes Agent or similar AI tooling
- **时间投入:** 全职 2-3 周 MVP；兼职 1-2 个月
- **成本:** <$50（域名 $10/yr + Cloudflare free + Vercel free）
- **预期 ROI:** 3 个月 >$100/mo（保守），6 个月 >$500/mo（aggressive but doable）

---

## 附录：可复用代码模板

### A1: sitemap.ts (Next.js App Router)

完整 sitemap 生成，含 hreflang alternates（EN ↔ ZH）。

```typescript
// app/sitemap.ts
import { MetadataRoute } from 'next';

const BASE_URL = 'https://audiotest.io';

// 定义所有路由（不含 locale 前缀）
const routes = [
  '/',
  '/tone-generator',
  '/frequency-sweep',
  '/bass-test',
  '/headphone-test',
  '/tinnitus-test',
  '/soundcheck',
  '/blog/wired-vs-wireless',
  '/blog/how-to-test-headphones',
  // ... 添加所有 blog posts
];

const locales = ['en', 'zh'];
const defaultLocale = 'en';

export default function sitemap(): MetadataRoute.Sitemap {
  const entries: MetadataRoute.Sitemap = [];

  routes.forEach((route) => {
    locales.forEach((locale) => {
      const isDefault = locale === defaultLocale;
      const path = isDefault ? route : `/${locale}${route}`;
      const url = `${BASE_URL}${path}`;

      // 为每个 locale 生成 alternate links
      const alternates: { languages: Record<string, string> } = {
        languages: {},
      };
      locales.forEach((altLocale) => {
        const altIsDefault = altLocale === defaultLocale;
        const altPath = altIsDefault ? route : `/${altLocale}${route}`;
        alternates.languages[altLocale] = `${BASE_URL}${altPath}`;
      });

      entries.push({
        url,
        lastModified: new Date(),
        changeFrequency: route === '/' ? 'daily' : 'weekly',
        priority: route === '/' ? 1.0 : 0.8,
        alternates,
      });
    });
  });

  return entries;
}
```

**Pitfall:** 如果你手动维护 `routes` 数组，每次加新页面要记得更新。Better: 动态读 `app/[locale]/*` 目录结构生成（但要 exclude `layout.tsx`, `error.tsx` 等）。

---

### A2: lib/gtag.ts (GA4 event tracking 封装)

类型安全的 GA4 event wrapper。

```typescript
// lib/gtag.ts
declare global {
  interface Window {
    gtag?: (
      command: 'event' | 'config',
      eventName: string,
      params?: Record<string, any>
    ) => void;
  }
}

export const GA_MEASUREMENT_ID = process.env.NEXT_PUBLIC_GA_ID || '';

type AffiliateEventParams = {
  product_name: string;
  product_tier: 'budget' | 'mid' | 'premium' | 'accessory';
  product_price?: string;
  product_rating?: number;
  page: string;
  position: number;
  locale: string;
  link_url?: string;
};

export function trackAffiliateImpression(params: AffiliateEventParams) {
  if (typeof window.gtag === 'function') {
    window.gtag('event', 'affiliate_impression', params);
  }
}

export function trackAffiliateClick(params: AffiliateEventParams) {
  if (typeof window.gtag === 'function') {
    window.gtag('event', 'affiliate_click', params);
  }
}

// 通用 event 追踪
export function trackEvent(eventName: string, params?: Record<string, any>) {
  if (typeof window.gtag === 'function') {
    window.gtag('event', eventName, params);
  }
}
```

**Usage:**
```tsx
import { trackAffiliateImpression, trackAffiliateClick } from '@/lib/gtag';

// In component
useEffect(() => {
  trackAffiliateImpression({
    product_name: 'Audio-Technica ATH-M50X',
    product_tier: 'mid',
    product_price: '$149',
    page: '/',
    position: 0,
    locale: 'en',
  });
}, []);

<a onClick={() => trackAffiliateClick({...})}>View on Amazon</a>
```

---

### A3: components/AffiliateCard.tsx (产品卡片 + 事件追踪)

完整的 affiliate card 实现，含 impression dedup + click tracking。

```tsx
'use client';
import { useEffect, useRef } from 'react';
import { trackAffiliateImpression, trackAffiliateClick } from '@/lib/gtag';

type Product = {
  asin: string;
  title: string;
  price: string;
  rating?: number;
  tier: 'budget' | 'mid' | 'premium' | 'accessory';
  imageUrl: string;
  localImage?: string;
};

type Props = {
  product: Product;
  position: number;
  page: string;
  locale?: string;
  compact?: boolean;
};

export function AffiliateCard({ product, position, page, locale = 'en', compact = false }: Props) {
  const impressionFired = useRef(false);
  const affiliateUrl = `https://www.amazon.com/dp/${product.asin}?tag=audiotest-20`;

  // Fire impression event once per mount
  useEffect(() => {
    if (!impressionFired.current && typeof window.gtag === 'function') {
      trackAffiliateImpression({
        product_name: product.title,
        product_tier: product.tier,
        product_price: product.price,
        product_rating: product.rating,
        page,
        position,
        locale,
      });
      impressionFired.current = true;
    }
  }, [product, page, position, locale]);

  const handleClick = () => {
    trackAffiliateClick({
      product_name: product.title,
      product_tier: product.tier,
      product_price: product.price,
      page,
      position,
      locale,
      link_url: affiliateUrl,
    });
  };

  const imgSrc = product.localImage || product.imageUrl;

  if (compact) {
    return (
      <a
        href={affiliateUrl}
        target="_blank"
        rel="nofollow noopener sponsored"
        onClick={handleClick}
        className="flex items-center gap-2 p-2 rounded border border-gray-700 hover:border-cyan-500 transition"
      >
        <img src={imgSrc} alt={product.title} className="w-12 h-12 object-contain" />
        <div className="flex-1 min-w-0">
          <p className="text-xs truncate">{product.title}</p>
          <p className="text-sm text-amber-400">{product.price}</p>
        </div>
      </a>
    );
  }

  return (
    <a
      href={affiliateUrl}
      target="_blank"
      rel="nofollow noopener sponsored"
      onClick={handleClick}
      className="block p-4 rounded-lg border border-gray-700 hover:border-cyan-500 transition group"
    >
      <img src={imgSrc} alt={product.title} className="w-full h-40 object-contain mb-3" />
      <h3 className="text-sm font-medium line-clamp-2 mb-2">{product.title}</h3>
      <div className="flex items-center justify-between">
        <span className="text-lg text-amber-400 font-semibold">{product.price}</span>
        {product.rating && (
          <span className="text-xs text-gray-400">★ {product.rating}</span>
        )}
      </div>
      <span className="text-xs text-cyan-500 mt-2 inline-block group-hover:underline">
        View on Amazon →
      </span>
    </a>
  );
}
```

**Pitfall:** 如果你用 CSS `hidden lg:block` 渲染 mobile/desktop 两个实例，impression 会 double count。Fix: 用 `useSyncExternalStore` + `matchMedia` conditional render（详见阶段 6 pitfalls）。

---

### A4: Daily report HTML template (Visual dashboard)

暗黑风格 HTML 模板，Playwright screenshot ready。

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      background: #0A0E17;
      color: #E2E8F0;
      font-family: 'Inter', -apple-system, sans-serif;
      padding: 40px;
      min-height: 100vh;
    }
    .container { max-width: 1200px; margin: 0 auto; }
    h1 {
      font-size: 32px;
      font-weight: 700;
      margin-bottom: 8px;
      background: linear-gradient(135deg, #06B6D4, #10B981);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .date { color: #64748B; font-size: 14px; margin-bottom: 40px; }
    .section {
      background: #111827;
      border: 1px solid #1E293B;
      border-radius: 12px;
      padding: 24px;
      margin-bottom: 24px;
    }
    .section-title {
      font-size: 18px;
      font-weight: 600;
      margin-bottom: 16px;
      color: #06B6D4;
    }
    .metric-row {
      display: flex;
      gap: 16px;
      margin-bottom: 12px;
    }
    .metric {
      flex: 1;
      background: #1E293B;
      padding: 16px;
      border-radius: 8px;
    }
    .metric-label {
      font-size: 12px;
      color: #64748B;
      text-transform: uppercase;
      margin-bottom: 4px;
    }
    .metric-value {
      font-size: 28px;
      font-weight: 700;
      font-family: 'JetBrains Mono', monospace;
    }
    .metric-change {
      font-size: 12px;
      margin-top: 4px;
    }
    .metric-change.up { color: #10B981; }
    .metric-change.down { color: #EF4444; }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 12px;
    }
    th, td {
      text-align: left;
      padding: 8px 12px;
      border-bottom: 1px solid #1E293B;
    }
    th {
      font-size: 12px;
      color: #64748B;
      text-transform: uppercase;
      font-weight: 600;
    }
    td {
      font-size: 14px;
      font-family: 'JetBrains Mono', monospace;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>audiotest.io Daily Report</h1>
    <div class="date">2026-06-12</div>

    <div class="section">
      <div class="section-title">📊 Traffic</div>
      <div class="metric-row">
        <div class="metric">
          <div class="metric-label">Visitors</div>
          <div class="metric-value">127</div>
          <div class="metric-change up">+12% vs yesterday</div>
        </div>
        <div class="metric">
          <div class="metric-label">Pageviews</div>
          <div class="metric-value">203</div>
          <div class="metric-change up">+8%</div>
        </div>
        <div class="metric">
          <div class="metric-label">Bounce</div>
          <div class="metric-value">67%</div>
          <div class="metric-change down">-3%</div>
        </div>
      </div>
    </div>

    <div class="section">
      <div class="section-title">🛒 Affiliate Funnel</div>
      <div class="metric-row">
        <div class="metric">
          <div class="metric-label">Impressions</div>
          <div class="metric-value">484</div>
        </div>
        <div class="metric">
          <div class="metric-label">Clicks</div>
          <div class="metric-value">9</div>
          <div class="metric-change">CTR 1.86%</div>
        </div>
      </div>
      <table>
        <thead>
          <tr><th>Product</th><th>Impr</th><th>Clicks</th><th>CTR</th></tr>
        </thead>
        <tbody>
          <tr><td>ATH-M50X</td><td>120</td><td>4</td><td>3.3%</td></tr>
          <tr><td>FiiO KA1</td><td>98</td><td>3</td><td>3.1%</td></tr>
        </tbody>
      </table>
    </div>

    <div class="section">
      <div class="section-title">🔍 SEO (GSC — last 7 days)</div>
      <table>
        <thead>
          <tr><th>Query</th><th>Pos</th><th>Impr</th><th>Clicks</th><th>CTR</th></tr>
        </thead>
        <tbody>
          <tr><td>audiotest</td><td>29</td><td>5</td><td>0</td><td>0%</td></tr>
          <tr><td>audio test</td><td>22</td><td>1</td><td>0</td><td>0%</td></tr>
        </tbody>
      </table>
    </div>
  </div>
</body>
</html>
```

**Generate screenshot:**
```bash
npx playwright screenshot --full-page report.html report.png
```

**Pitfall:** 忘记 `--full-page` → 只截图首屏 600px。David 明确要求全页截图。

---

### A5: Python script — Batch create Linear issues with labels

绕过 `linear_api.py` 的 `--label` stub，直接用 GraphQL。

```python
#!/usr/bin/env python3
import json, urllib.request, pathlib, yaml

# Read LINEAR_API_KEY
cfg = {}
env_path = pathlib.Path.home() / '.hermes' / '.env'
if env_path.exists():
    for line in env_path.read_text().splitlines():
        line = line.strip()
        if line and not line.startswith('#') and '=' in line:
            k, v = line.split('=', 1); cfg[k.strip()] = v.strip()
yaml_data = yaml.safe_load(open(pathlib.Path.home()/'.hermes'/'config.yaml')) or {}
for k, v in yaml_data.items():
    if isinstance(v, str): cfg[k] = v.strip()

api_key = cfg['LINEAR_API_KEY']

def gql(query, variables=None):
    body = json.dumps({"query": query, "variables": variables or {}}).encode()
    req = urllib.request.Request(
        "https://api.linear.app/graphql",
        data=body,
        headers={"Authorization": api_key, "Content-Type": "application/json"}
    )
    return json.loads(urllib.request.urlopen(req, timeout=20).read())

# Example: Create issue with label
mutation = """
mutation($input: IssueCreateInput!) {
  issueCreate(input: $input) {
    success
    issue { id identifier title url }
  }
}
"""

inp = {
    "teamId": "YOUR_TEAM_ID",
    "projectId": "YOUR_PROJECT_ID",
    "stateId": "YOUR_TODO_STATE_ID",
    "title": "Example issue",
    "description": "Issue body",
    "priority": 2,
    "labelIds": ["YOUR_LABEL_ID"],
}

result = gql(mutation, {"input": inp})
print(result)
```

**To get IDs:**
```python
# Teams
gql('{ teams { nodes { id key name } } }')

# States
gql('{ workflowStates(filter: { team: { key: { eq: "DLS" } } }) { nodes { id name type } } }')

# Labels
gql('{ issueLabels { nodes { id name } } }')

# Projects
gql('{ projects(filter: { name: { eq: "audiotest.io" } }) { nodes { id name } } }')
```

---

## 参考资料

- audiotest.io 实战复盘（2026-06-12）
- Hermes skills: `affiliate-growth-analytics`, `vercel-deploy`, `nextjs-seo`, `github-pr-workflow`, `linear`, `humanizer`
- Niche site case studies: Niche Pursuits, Empire Flippers blog, Authority Hacker
- SEO 长尾词策略: Ahrefs blog "Long-tail keywords" guide

