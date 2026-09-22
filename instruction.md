# 博客操作指南

## 一、如何写一篇新文章并放到 casual_notes 里

### 第 1 步：创建 Markdown 文件

在 `docs/casual_notes/` 下新建一个 `.md` 文件。

例如想写一篇标题为"我的旅行日记"的文章，就创建：

```
docs/casual_notes/travel_diary.md
```

文件内容用 Markdown 写：

```markdown
# 我的旅行日记

今天去了一个很有意思的地方...

## 行程安排

- 早上 8 点出发
- 中午到达目的地
- 下午返程

## 感想

这次旅行让我学到了很多。
```

**注意：** 文件第一行的 `# 标题` 就是文章的标题，会显示在页面顶部和侧边栏中。

### 第 2 步：在 mkdocs.yml 中注册

打开 `mkdocs.yml`，找到 `nav` 部分的 `casual_notes`，添加新条目：

```yaml
nav:
  - casual_notes:
    - casual_notes/index.md
    - 我的旅行日记: casual_notes/travel_diary.md    # ← 新增这一行
```

格式是：

```
- 侧边栏显示的名称: 文件路径（相对于 docs/ 目录）
```

### 第 3 步：推送

```bash
git add .
git commit -m "add: travel diary"
git push
```

完成！文章会出现在 casual_notes 页面，侧边栏也会显示"我的旅行日记"。

---

## 二、如何在 casual_notes 下建子分类

如果文章多了想分组，可以建子文件夹。

### 示例：建一个"随笔"子分类

**第 1 步：** 创建文件夹和文件

```
docs/casual_notes/essays/
├── index.md              ← 子分类的首页
├── thought_1.md          ← 子分类下的文章
└── thought_2.md
```

**第 2 步：** 在 mkdocs.yml 中注册

```yaml
nav:
  - casual_notes:
    - casual_notes/index.md
    - 我的旅行日记: casual_notes/travel_diary.md
    - 随笔:                                    # ← 子分类名称
      - casual_notes/essays/index.md           # ← 子分类首页
      - 思考一: casual_notes/essays/thought_1.md
      - 思考二: casual_notes/essays/thought_2.md
```

侧边栏会显示为：

```
casual_notes
├── 我的旅行日记
└── 随笔              ← 可展开的子分类
    ├── 思考一
    └── 思考二
```

---

## 三、其他篇章同理

所有篇章（as_student、as_staff、as_reader、as_foreigner、casual_notes）的操作方式完全一样：

1. 在 `docs/对应篇章/` 下创建 `.md` 文件
2. 在 `mkdocs.yml` 的 `nav` 中注册
3. `git push`

---

## 四、Markdown 常用语法速查

```markdown
# 一级标题（文章标题）
## 二级标题
### 三级标题

**加粗文字**
*斜体文字*

- 无序列表项 1
- 无序列表项 2

1. 有序列表项 1
2. 有序列表项 2

[链接文字](https://example.com)

![图片描述](assets/images/图片.png)

> 引用文字

`行内代码`

```python
# 代码块
print("hello")
```

---

## 五、数学公式

```markdown
行内公式：$E = mc^2$

块级公式：
$$
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
$$
```

---

## 六、图片

把图片放到 `docs/assets/images/` 下，然后在 Markdown 中引用：

```markdown
![描述](assets/images/my-photo.png)
```

如果用 Obsidian 写笔记，可以直接 Ctrl+V 粘贴截图（需设置附件目录为 `docs/assets/images/`）。

---

## 七、提示框

```markdown
!!! note "提示标题"
    这是提示内容

!!! warning "注意"
    这是警告内容

??? info "可折叠"
    点击展开
```

---

## 八、完整示例：从零添加一篇文章

假设要在 as_student 下添加一篇"线性代数笔记"：

**1. 创建文件** `docs/as_student/linear_algebra.md`

```markdown
# 线性代数笔记

## 第一章 行列式

行列式的定义...

## 第二章 矩阵

矩阵的基本运算...
```

**2. 修改 mkdocs.yml**

```yaml
nav:
  - as_student:
    - as_student/index.md
    - 前言: as_student/preface.md
    - 线性代数: as_student/linear_algebra.md    # ← 新增
    - 计算机组成原理:
      - as_student/computer_organization/index.md
```

**3. 推送**

```bash
git add docs/as_student/linear_algebra.md mkdocs.yml
git commit -m "add: linear algebra notes"
git push
```

侧边栏会显示：

```
as_student
├── 前言
├── 线性代数        ← 新文章
└── 计算机组成原理
```
