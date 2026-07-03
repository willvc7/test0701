> 冷調專業基底 + 暖陶土連結點綴

---

## 1. `quartz.config.yaml` — 主題設定

### 字型

| 用途 | 字型 |
|------|------|
| Header | Inter |
| Body | Inter |
| Code | IBM Plex Mono |

### 色碼

| 變數              | Light Mode                  | Dark Mode                   | 用途                          |
| --------------- | --------------------------- | --------------------------- | --------------------------- |
| `light`         | `#f4f5f7`                   | `#16191d`                   | 頁面背景                        |
| `lightgray`     | `#e2e4e8`                   | `#2c3038`                   | 卡片／側欄背景                     |
| `gray`          | `#b0b5bd`                   | `#5a606a`                   | 邊框／分隔線                      |
| `darkgray`      | `#585d66`                   | `#c5cad4`                   | 次要文字                        |
| `dark`          | `#23262b`                   | `#e0e4ea`                   | 主要文字（標題、粗體）                 |
| `secondary`     | `#5b7a8f`                   | `#7a9aaa`                   | 重點色（blockquote、checkbox、標籤） |
| `tertiary`      | `#8a9aa5`                   | `#8da0b0`                   | 輔助色（hover、選取）               |
| `highlight`     | `rgba(130, 150, 170, 0.12)` | `rgba(130, 150, 175, 0.15)` | 高亮背景（程式碼行、nav active）       |
| `textHighlight` | `#d4c8a888`                 | `#9aa88888`                 | 螢光筆標記                       |

---

## 2. `custom.scss` — 內文連結覆寫

僅影響 `article` 內的連結，側欄、nav、footer、backlinks 維持 Arctic Slate 原本的灰藍色。

```scss
:root {
  --content-link: #c46a4a;
  --content-link-hover: #b05a38;
}

:root[saved-theme="dark"] {
  --content-link: #dba568;
  --content-link-hover: #c89054;
}

article a {
  color: var(--content-link);

  &:hover {
    color: var(--content-link-hover);
  }

  &.internal {
    background-color: color-mix(in srgb, var(--content-link) 15%, transparent);
  }
}
```

### 連結色對照

| 模式 | 一般連結 | Hover | Internal Link 背景 |
|------|---------|-------|-------------------|
| Light | `#c46a4a` 暖陶土 | `#b05a38` 深陶土 | 陶土色 15% 透明 |
| Dark | `#dba568` 暖琥珀 | `#c89054` 深琥珀 | 琥珀色 15% 透明 |

---

## 3. 設計邏輯

- **基底 Arctic Slate**：低飽和灰藍冷色調，營造冷靜專業感（避免常見的亮藍）
- **字型 Inter**：乾淨現代，與冷色調一致
- **內文連結暖色點綴**：light mode 陶土紅、dark mode 琥珀金，在冷底上形成舒適對比
- **只改 `article a`**：sidebar、explorer、footer、tags、graph 節點不受影響
