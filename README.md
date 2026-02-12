[English](./README.md) | [中文](./README_zh.md)

# Seedance Prompt Skill for Claude Code

A Claude Code custom skill that turns Claude into a professional AI video prompt engineer for ByteDance's **Seedance 2.0** (即梦) video generation platform.

Provide a creative idea in natural language, and this skill will generate structured, production-ready Chinese prompts that you can paste directly into the Seedance 2.0 platform to produce cinematic AI videos.

## Features

### Ten Core Prompt Generation Capabilities

| # | Capability | Description |
|---|-----------|-------------|
| 1 | **Pure Text Generation** | Generate videos purely from text descriptions, no reference materials needed |
| 2 | **Consistency Control** | Maintain character/product/scene consistency across shots using reference images |
| 3 | **Camera & Motion Replication** | Replicate camera movements, complex actions, and pacing from reference videos |
| 4 | **Creative Template / VFX Replication** | Reproduce creative transitions, ad templates, and cinematic effects from reference videos |
| 5 | **Story Completion** | Auto-generate storylines from storyboard images or scripts |
| 6 | **Video Extension** | Extend existing videos forward or backward with smooth continuity |
| 7 | **Sound Control** | Voice cloning, dialogue generation, and sound effect design |
| 8 | **One-Take Long Shot** | Generate seamless long takes that flow continuously across scenes |
| 9 | **Video Editing** | Modify existing videos: swap characters, alter plots, add/remove elements |
| 10 | **Music Beat Sync** | Synchronize visual rhythm precisely with music beats |

### Advanced Techniques

- **Timestamp Storyboarding** — Precise per-second control for 15-second videos (e.g., `0-3s: ...`, `4-8s: ...`)
- **Technical Parameter Specification** — Set aspect ratio, frame rate, color grading, and lens style upfront
- **Negative Prompting** — Explicitly exclude unwanted elements (watermarks, subtitles, etc.)
- **Multi-Segment Stitching** — Automatically split videos longer than 15 seconds into extension-chained segments with continuity notes

### Multi-Modal Reference System

Supports the Seedance 2.0 `@` reference syntax for combining multiple input modalities:

- **Images** (`@图片1` ~ `@图片9`) — Character references, scene backgrounds, first/last frame control
- **Videos** (`@视频1` ~ `@视频3`) — Camera motion, action, effects, and pacing references
- **Audio** (`@音频1` ~ `@音频3`) — Background music, voice tone, sound effect references

### Scenario-Specific Prompt Strategies

- **E-commerce / Advertising** — Product showcases, 360-degree spins, 3D exploded views
- **Short Drama / Dialogue** — Scripted scenes with character dialogue, emotion tags, and sound design
- **Xianxia / Fantasy Animation** — Cinematic martial arts, spell effects, transformation sequences
- **Science Education** — 4K medical CGI, transparent anatomy visualizations
- **Music Videos / Beat Sync** — Widescreen compositions, multi-image beat matching

### Built-in Prompt Asset Libraries

The skill ships with curated vocabularies for:

- **Camera Language** — Shot types, camera movements, angles, pacing, focus, transitions
- **Visual Styles** — Film grains, color palettes, art movements, lighting setups, animation styles

## Installation

### Prerequisites

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- A Seedance 2.0 (即梦) account at [jimeng.jianying.com](https://jimeng.jianying.com) for using the generated prompts

### Steps

1. **Clone the repository**

```bash
git clone https://github.com/<your-username>/seedance-prompt-skill.git
```

2. **Copy the skill into your project's `.claude/skills/` directory**

```bash
# Navigate to the project where you want to use the skill
cd /path/to/your/project

# Create the skills directory if it doesn't exist
mkdir -p .claude/skills/seedance

# Copy the skill file
cp /path/to/seedance-prompt-skill/.claude/skills/seedance/SKILL.md .claude/skills/seedance/SKILL.md
```

3. **Register the skill in your Claude Code settings**

Create or edit `.claude/settings.local.json` in your project root:

```json
{
  "permissions": {
    "allow": [
      "WebSearch"
    ]
  }
}
```

> `WebSearch` permission is optional but recommended — it allows the skill to look up the latest Seedance platform updates if needed.

4. **Verify installation**

Start Claude Code in your project directory:

```bash
claude
```

Then type `/seedance` or simply describe your video idea. Claude should activate the Seedance prompt skill automatically.

### Alternative: Global Installation

To make the skill available across all your projects, place it under your home directory:

```bash
mkdir -p ~/.claude/skills/seedance
cp /path/to/seedance-prompt-skill/.claude/skills/seedance/SKILL.md ~/.claude/skills/seedance/SKILL.md
```

## Usage

### Quick Start

Start Claude Code and describe what video you want to create:

```
You: 帮我生成一段赛博朋克风格的城市夜景视频提示词
```

Claude will ask you a few clarifying questions (duration, aspect ratio, reference materials), then generate 2-3 prompt versions ready to paste into Seedance 2.0.

### Triggering the Skill

The skill activates automatically when you:

- Use the `/seedance` command
- Mention keywords like: `Seedance`, `即梦`, `视频提示词`, `视频生成`, `AI视频`, `短剧`, `广告视频`, `视频延长`
- Ask to "generate video prompts" or "create Seedance prompts"

### Interactive Workflow

The skill follows a structured 4-step workflow:

```
Step 1: You describe your idea → "一段古风武侠打斗"
Step 2: Claude confirms parameters → duration, aspect ratio, references, style preferences
Step 3: Claude generates prompts → 2-3 versions for videos ≤15s, or multi-segment plan for longer videos
Step 4: You refine → adjust timing, camera, dialogue, effects, or style
```

## Examples

### Example 1: Pure Text — Short Action Scene

**Input:**

```
帮我写一段仙侠战斗的视频提示词，15秒，横屏
```

**Output (one of 2-3 versions):**

```
15秒仙侠高燃战斗镜头，金红暖色调，0-3秒：低角度特写主角蓝袍衣摆被热浪吹得猎猎飘动，
双手紧握雷纹巨剑，剑刃赤红电光持续爆闪，地面熔岩翻涌冒泡，远处魔兵嘶吼着冲锋逼近，
主角低喝"今日，便以这柄剑，镇尔等邪祟！"，伴随剑鸣与熔岩咕嘟声；4-8秒：环绕摇镜
快切，主角旋身挥剑，剑刃撕裂空气迸射红色冲击波，前排魔兵被击飞碎裂成灰烬，伴随剑气
破空声与魔兵惨嚎；9-12秒：仰拍拉远定格慢放，主角跃起腾空，剑刃凝聚巨型雷光电弧劈
向魔兵群；13-15秒：缓推特写主角落地收剑的姿态，衣摆余波微动，冷声道"此界之门，
不容踏越"，音效收束为余音震颤与渐弱风声。
```

### Example 2: Multi-Modal Reference — Product Ad

**Input:**

```
我有一张可乐产品图，想做一个炫酷的产品展示广告
```

**Output:**

```
@图片1中的可口可乐饮料，360度高速旋转2圈后，突然停住蓄力分裂成了3个部分进行展示。
随后分解后的可口可乐饮料罐的上中下三部分快速向内旋转合成，一罐完整的可口可乐饮料，
3D渲染产品展示特效，动感产品特效展示

参考素材：
- @图片1：可乐产品正面高清图
```

### Example 3: Short Drama with Dialogue

**Input:**

```
写一段霸道总裁短剧，15秒，女主撕合同反杀的名场面
```

**Output:**

```
画面（0-5秒）：特写女主撕契约镜头，纸屑飘落，总裁单膝跪地伸手阻拦，眼神慌乱，
女主侧身躲开，嘴角挂着冷漠笑意
台词1（总裁，卑微慌乱）：苏晚！契约还没结束，你不能走！我给你钱，给你地位！
画面（6-10秒）：女主抬脚避开他的手，将撕碎的契约纸扔在他脸上，镜头扫过周围宾客的
窃窃私语
台词2（女主，冷漠反杀）：契约？顾总，当初是你说，我连给你提鞋都不配，现在求我？晚了！
画面（11-15秒）：总裁僵在原地，脸上沾着纸屑，女主转身昂首离开，红裙裙摆飘动
音效：华丽又带张力的背景音，契约撕碎的声响，宾客轻微的窃窃私语声
时长：精准15秒
```

### Example 4: Long Video (>15s) — Multi-Segment

**Input:**

```
做一段30秒的仙侠出场短片
```

**Output:**

```
## 超长视频提示词（总时长约30秒）

**主题**：剑修云海仙山迎敌
**总段数**：2段
**建议比例**：16:9

---

### 第1段（0-15秒）—— 正常生成

**生成时长**：15秒

#### 提示词

15秒仙侠镜头，0-5秒：俯拍云海翻涌中的仙山全景，镜头缓缓下推穿过云层；
6-10秒：剑修站在山巅悬崖边，背对镜头，衣袍随风飘动，远处魔气升腾；
11-15秒：剑修缓缓转身面向镜头，拔剑出鞘，剑刃金光闪烁，目光坚毅低声道
"来了"，定格在剑修持剑面向镜头的画面。

#### 衔接点

本段结尾画面：剑修正面持剑站在山巅，目光前视，远方魔气翻涌。

---

### 第2段（15-30秒）—— 视频延长

**操作**：将第1段生成的视频上传为 @视频1
**生成时长**：15秒

#### 提示词

将@视频1延长15秒。0-5秒：接上段剑修持剑画面，数十只暗影魔兽从远处魔气中
飞扑而来，剑修纵身跃起迎敌；6-10秒：空中激战，剑气纵横，魔兽被斩成灰烬
粒子消散，镜头环绕快切；11-15秒：剑修落地收剑，身后爆炸的金色粒子缓缓飘散，
镜头缓推特写剑修侧脸，音效渐弱。
```

### Example 5: One-Take Long Shot with Multi-Image References

**Input:**

```
我有5张图，想做一个一镜到底的谍战片追踪镜头
```

**Output:**

```
谍战片风格，@图片1作为首帧画面，镜头正面跟拍穿着红风衣的女特工向前走，
镜头全景跟随，不断有路人遮挡红衣女子，走到一个拐角处，参考@图片2的拐角建筑，
固定镜头红衣女子离开画面，走在拐角处消失，一个戴面具的女孩在拐角处躲着恶狠狠
的盯着她，面具女孩形象参考@图片3。镜头往前摇向红衣女特工，她走进一座豪宅
消失不见了，豪宅参考@图片4。全程不要切镜头，一镜到底。

参考素材：
- @图片1：红风衣女特工正面形象（首帧）
- @图片2：旧城区拐角建筑
- @图片3：面具女孩形象
- @图片4：欧式豪宅外观
- @图片5：备用场景（可用于扩展）
```

## Seedance 2.0 Platform Specs

| Dimension | Specification |
|-----------|--------------|
| Image Input | jpeg/png/webp/bmp/tiff/gif, up to 9 images, each <30MB |
| Video Input | mp4/mov, up to 3 videos, total 2-15s, each <50MB, 480p-720p |
| Audio Input | mp3/wav, up to 3 files, total ≤15s, each <15MB |
| Text Input | Natural language description |
| File Limit | Max 12 files total (images + videos + audio combined) |
| Duration | 4-15 seconds per generation |
| Sound Output | Built-in sound effects and music |
| Resolution | Up to 2K output |

> **Important:** The platform does not allow uploading images or videos containing realistic human faces. Such materials will be automatically blocked.

## Tips for Best Results

- **Be specific and visual** — "a woman in a red trench coat walks through rain-soaked neon streets" works much better than "a woman walking"
- **Use timestamp storyboarding** for 13-15 second videos to maintain control over each segment
- **Separate dialogue and sound effects** from visual descriptions for cleaner results
- **Specify negative constraints** at the end (e.g., "no watermarks, no subtitles, no text overlays")
- **Match reference image styles** to your video theme (e.g., use ink-wash style images for Chinese historical themes)
- **For videos over 15 seconds**, let the skill generate multi-segment plans with explicit continuity points between segments

## Project Structure

```
.
├── .claude/
│   ├── settings.local.json       # Claude Code local permissions
│   └── skills/
│       └── seedance/
│           └── SKILL.md           # The skill definition (core file)
├── .gitignore
└── README.md
```

The entire skill logic is contained in a single file: `.claude/skills/seedance/SKILL.md`.

## Contributing

Contributions are welcome. Some areas where help would be appreciated:

- Adding more prompt examples for specific scenarios
- Translating the skill definition to support English prompt generation
- Adding prompt templates for new Seedance features as the platform evolves
- Improving prompt quality based on real-world generation results

To contribute:

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m "Add your feature"`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

## License

MIT

## Acknowledgments

- [Seedance 2.0](https://jimeng.jianying.com) by ByteDance for the AI video generation platform
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) by Anthropic for the extensible skill system
