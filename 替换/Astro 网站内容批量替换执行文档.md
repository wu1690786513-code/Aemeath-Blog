## 文档用途
专为**Agent 批量替换网站内容**定制，**直接按照本文档填写新内容**，即可全自动精准替换所有配置，无需手动修改代码，适配 Astro 框架项目。

## 一、待替换文件总览
所有修改涉及以下核心配置文件：
1. `src/config/siteConfig.ts`（网站基础配置 + Bangumi配置）
2. `src/config/backgroundWallpaper.ts`（壁纸+主页横幅配置）
3. `src/config/profileConfig.ts`（站长个人信息配置）
4. `src/config/fontConfig.ts`（字体自定义配置）
5. `src/config/footerConfig.ts`（页脚自定义配置）
6. `src/config/musicConfig.ts`（音乐配置）
7. `src/config/FooterConfig.html`（页脚HTML内容）

* 图片路径支持三种格式：
     1. public 目录（以 "/" 开头，不优化）："/assets/images/banner.avif"
     2. src 目录（不以 "/" 开头，自动优化但会增加构建时间，推荐）："assets/images/banner.avif"
     3. 远程 URL："https://example.com/banner.jpg"


## 二、逐项填写新内容（直接替换下方占位内容即可）
### 1. 网站 Favicon
**文件路径**：src/config/siteConfig.ts
**配置项**：favicon.src
**新 favicon 路径/链接**：
```
https://upload.codexing.top/Sigrika/aemeath-avatar.webp
```

---

### 2. 导航栏 Logo
**文件路径**：src/config/siteConfig.ts
**新 Logo 路径/链接**：
```
aemeath.gif
```

---

### 3. 站点基础信息
**文件路径**：src/config/siteConfig.ts
**配置项**：siteConfig 对象
- **站点标题(title)**：
```
Aemeath
```
- **站点副标题(subtitle)**：
```
宝贝回家
```
- **站点链接(site_url)**：
```
https://aemeath.sigrika.cc
```
- **站点描述(description)**：
```
记录我的二次元之旅
```
- **网站主题色(themeColor)**：
```
360
```

---

### 4. 网站壁纸
**文件路径**：src/config/backgroundWallpaper.ts
**配置项**：backgroundWallpaper 对象
>先把素材文件夹下的图片自动按顺序命名为1、2、3、4、5.webp
再复制到对应文件夹
- **电脑端壁纸(desktop)**：
```
assets/images/DesktopWallpaper/1.webp
assets/images/DesktopWallpaper/2.webp
assets/images/DesktopWallpaper/3.webp
assets/images/DesktopWallpaper/4.webp
assets/images/DesktopWallpaper/5.webp
```
- **手机端壁纸(mobile)**：
```
assets/images/MobileWallpaper/1.webp
assets/images/MobileWallpaper/2.webp
assets/images/MobileWallpaper/3.webp
assets/images/MobileWallpaper/4.webp
assets/images/MobileWallpaper/5.webp
```
✅ 壁纸模式固定为 banner，无需修改

---

### 5. 主页横幅标题
**文件路径**：src/config/backgroundWallpaper.ts
- **主页横幅主标题(title)**：
```
Aemeath
```
- **主页横幅副标题(subtitle)**：
```
宝贝回家
```

---

### 6. 站长个人信息
**文件路径**：src/config/profileConfig.ts
- **站长名字(name)**：
```
Aemeath
```
- **个人签名(bio)**：
```
嘻嘻
```
- **站长头像(avatar)**：
```
https://upload.codexing.top/Sigrika/aemeath-avatar.webp
```

---

### 7. 字体自定义配置
**文件路径**：src/config/fontConfig.ts
- **开启字体自定义**：
```
enable: true,
selected: ["lxgw-wenkai-screen"],
```
- **在 fonts 对象中添加**：
```typescript
"lxgw-wenkai-screen": {
    id: "lxgw-wenkai-screen",
    name: "霞鹜文楷 屏幕版",
    src: "https://cdn.bootcdn.net/ajax/libs/lxgw-wenkai-screen-webfont/1.7.0/style.min.css",
    family: "LXGW WenKai Screen",
    weight: 400,
    display: "swap" as const,
},
```

---

### 8. 页脚自定义配置
**文件路径**：src/config/footerConfig.ts
- **开启页脚自定义**：
```
enable: true,
```

**文件路径**：src/config/FooterConfig.html
- **添加以下内容**：
```html
<div style="width: 100%; margin: 15px 0; text-align: center;">

  <!-- 萌ICP备案 -->
  
  <div style="margin-bottom: 8px;">
    <a href="https://icp.gov.moe/?keyword=20261087" target="_blank" style="display: inline-flex; align-items: center; gap: 6px; text-decoration: none; color: #666; font-size: 14px; vertical-align: middle;">
      <img src="https://icp.gov.moe/images/gov.svg" style="height: 18px;">
      <span>萌ICP备20261087号</span>
    </a>
  </div>
  
  <!-- 又拍云加速 -->
  <div style="margin-bottom: 10px;">
    <a href="https://www.upyun.com/league" target="_blank" style="display: inline-flex; align-items: center; gap: 6px; text-decoration: none; color: #666; font-size: 14px; vertical-align: middle;">
      本站由<img src="http://upload.codexing.top/Blogs/Sigrika/upyun.png" style="height: 25px;">提供图片加速服务
    </a>
  </div>
  
  <!-- 美化访客统计 -->
  <div style="letter-spacing:1px;cursor:pointer;" onclick="location.href='/guestbook/'">
    有幸与您相遇，您是本站第<span style="margin:0 4px;" id="vercount_value_site_uv">加载中...qwq</span>位访客
  </div>
</div>

<!-- 访客统计脚本 -->
<script>
  async function loadSitePV() {
    const elements_page_pv = document.querySelectorAll('[data-stat-id="vercount_value_page_pv"]');
    const elements_site_pv = document.querySelectorAll('[data-stat-id="vercount_value_site_pv"]');
    const host = window.location.host;
    const cookieKey = "vercount_uv_" + host;
    const isNewUv = !document.cookie.split("; ").find(i=>i.startsWith(cookieKey+"="));
    
    if (isNewUv) {
      document.cookie = `${cookieKey}=1; path=/; max-age=31536000; SameSite=Lax`;
    }
    
    try {
      const resp = await fetch('https://events.vercount.one/api/v2/log', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          url: window.location.href,
          isNewUv: isNewUv,
          onlyCount: false
        })
      });
      
      const data = await resp.json();
      const page_pv = data.data?.page_pv || 0;
      const site_pv = data.data?.site_pv || 0;
      const site_uv = data.data?.site_uv || 0;
      
      elements_page_pv.forEach(el => el.textContent = page_pv.toString());
      elements_site_pv.forEach(el => el.textContent = site_pv.toString());
      
      const elements_site_uv = document.getElementById('vercount_value_site_uv');
      if (elements_site_uv) {
        elements_site_uv.textContent = site_uv.toString();
      }
    } catch (e) {}
  }
  
  loadSitePV();
</script>
```

---

### 9. 音乐配置
**文件路径**：src/config/musicConfig.ts
- **网易云歌单ID**：
```
id: "你的网易云歌单id"
```

---

### 10. Bangumi 配置
**文件路径**：src/config/siteConfig.ts
- **Bangumi 用户 ID**：
```
userId: "你的bangumi ID"
```

---

## 三、Agent 执行规则（固定不变）
1. 严格按照**文件路径**定位文件，不修改路径层级
2. 仅替换**配置项的值**，不修改配置项名称、不删除代码
3. 所有字符串保持**英文引号包裹**，保持原代码格式
4. 修改完成后校验：无语法错误、引号闭合、逗号完整
5. 所有素材均需提前准备好并放置在正确的目录位置
