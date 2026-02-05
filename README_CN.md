# Read Document Skill

[English](./README.md)

Claude Code 技能，用于基于官方文档生成代码。此技能会获取官方文档并创建技术参考摘要，作为代码生成的前置步骤。

## 安装

```bash
npx skills add wxul/read-document-skill
```

### 手动安装

```bash
git clone https://github.com/wxul/read-document-skill.git
cp -r read-document-skill/skills/* .claude/skills/
```

## 工作原理

```
用户请求使用某技术生成代码
         ↓
    自动触发 Skill
         ↓
    推荐文档 URL
         ↓
  ┌──────┼──────┐
 确认   其他URL  忽略
  ↓       ↓       ↓
获取    获取    跳过
文档   其他URL  直接生成
  ↓       ↓
  └───┬───┘
      ↓
生成技术参考摘要
      ↓
使用摘要生成代码
```

## 使用方式

### 自动触发

当你提到某个技术栈并请求生成代码时，skill 会自动触发：

```
帮我用 GSAP 创建一个视差滚动效果
```

Claude 会：
1. 推荐 GSAP 文档地址
2. 询问你确认、提供其他地址、或忽略
3. 获取并总结相关文档
4. 使用摘要生成准确的代码

### 手动调用

```
/read-doc <技术栈> <需求>
```

## 示例

### 动画库

```
/read-doc gsap 创建滚动触发动画
```

```
/read-doc framer-motion 添加拖拽排序列表
```

### 状态管理

```
/read-doc zustand 创建带持久化的购物车状态
```

```
/read-doc jotai 用 atoms 管理表单状态
```

### 数据请求

```
/read-doc tanstack-query 实现带分页的用户数据获取和缓存
```

```
/read-doc swr 实现无限滚动加载
```

### UI 框架

```
/read-doc shadcn 创建命令面板组件
```

```
/read-doc radix-ui 构建无障碍下拉菜单
```

### 3D / 可视化

```
/read-doc three.js 创建带轨道控制的旋转 3D 立方体
```

```
/read-doc d3 构建交互式柱状图
```

### 表单验证

```
/read-doc react-hook-form 创建多步骤表单向导
```

```
/read-doc zod 定义用户注册校验规则
```

## 提示选项

当 skill 推荐文档 URL 时，你有三个选项：

| 选项 | 说明 |
|------|------|
| **Yes** | 使用推荐的 URL |
| **其他 URL** | 提供你自己的文档地址 |
| **Ignore** | 跳过文档获取，使用现有知识生成代码 |

## 输出

Skill 会生成技术参考摘要：

```markdown
## Technical Reference: [技术栈]

### Source
- [文档 URL]

### Relevant APIs
[API 签名、参数、返回类型]

### Usage Patterns
[文档中的代码示例]

### Best Practices
[文档中的最佳实践建议]

### Notes
[重要注意事项或版本相关信息]
```

此摘要将作为后续代码生成的参考。

## License

ISC
