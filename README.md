# FPOF — 와키윌리 패션 하우스 시스템

> **Fashion PDCA Orchestration Framework**
>
> AI가 와키윌리(Wacky Willy) 브랜드의 시즌 기획부터 런칭까지를 함께 운영하는 패션 하우스 오케스트레이션 시스템입니다.
>
> 패션 실무자가 자연어로 지시하면, 브랜드 DNA와 전략을 완벽히 숙지한 AI 전문가가 실무 산출물을 만듭니다.

---

## 📋 목차

1. [시스템 개요](#-시스템-개요)
2. [스킬 아키텍처](#-스킬-아키텍처)
3. [사용법](#-사용법)
4. [PDCA 워크플로우](#-pdca-워크플로우)
5. [스킬 전체 목록](#-스킬-전체-목록)
6. [명령어 가이드](#-명령어-가이드)
7. [폴더 구조](#-폴더-구조)

---

## 🎯 시스템 개요

### 핵심 개념

FPOF는 **3계층 스킬 아키텍처**로 구성된 패션 하우스 시스템입니다.

```
┌─────────────────────────────────────────────────────────────┐
│  Layer 1: FPOF Main Skills (skills/)                  │
│  ───────────────────────────────────────────────────────  │
│  21개 패션 실무 전용 스킬                              │
│  와키윌리 브랜드 DNA 내장                           │
│  PDCA 워크플로우 최적화                                 │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  Layer 2: Claude Universal Skills (.claude/skills/)      │
│  ───────────────────────────────────────────────────────  │
│  19개 범용 유틸리티 스킬                              │
│  모든 프로젝트에서 사용 가능                             │
│  문서 생성/디자인/개발 도구                             │
└─────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────┐
│  Layer 3: Adapters & Bridges (skills-universal/)        │
│  ───────────────────────────────────────────────────────  │
│  어댑터: 브랜드/모델 맞춤화                             │
│  브릿지: FPOF ↔ 유니버설 스킬 연계                      │
└─────────────────────────────────────────────────────────────┘
```

### 주요 특징

| 특징 | 설명 |
|------|------|
| **브랜드 중심** | 와키윌리 브랜드 DNA(Kitsch Street & IP Universe)가 모든 스킬에 내장 |
| **PDCA 워크플로우** | Plan → Design → Do → Check → Act 자동화 |
| **품질 게이트** | 각 단계 완료 시 자동 검수(QG1~QG4) |
| **자연어 라우팅** | 키워드 기반 에이전시/역할/스킬 자동 매핑 |
| **범용 유틸리티** | 19개 유니버설 스킬로 크로스 프로젝트 지원 |
| **상태 관리** | `.fpof-state.json`으로 실시간 진행 상황 추적 |

### 브랜드 정보

| 항목 | 내용 |
|------|------|
| **브랜드명** | 와키윌리 (Wacky Willy) |
| **컨셉** | Kitsch Street & IP Universe |
| **코어 타겟** | 18~25세 자유로운 트렌드리더 |
| **뮤즈** | 지젤 |
| **비전** | 2029 NO.1 K-Lifestyle Brand |
| **슬로건** | 규칙은 없어, 우리만의 놀이터로 초대할게! |

---

## 🏗️ 스킬 아키텍처

### Layer 1: FPOF Main Skills (21개)

**위치**: `skills/` 폴더
**목적**: 와키윌리 패션 하우스 전용 실무 스킬

| 에이전시 | 스킬 (4개) | 역할 | PDCA 단계 |
|----------|---------------|------|----------|
| **전략기획실** | trend-research, brand-strategy, md-planning, line-sheet | 시장 리서처, 브랜드 전략가, 수석 MD, 컬렉션 플래너 | Plan |
| **크리에이티브 스튜디오** | moodboard, design-spec, visual-generation | 크리에이티브 디렉터, 패션 디자이너, 아트 디렉터 | Design |
| **프로덕트 랩** | techpack, costing-ve, qr-process | 프로덕션 매니저 | Design/Do |
| **마케팅 쇼룸** | imc-strategy, visual-content, copywriting, social-viral | 마케팅 디렉터, 콘텐츠 디렉터, 패션 에디터, 소셜 전략 디렉터 | Do |
| **데이터 인텔리전스** | sales-analysis, insight-archiving | 트렌드 애널리스트, 인사이트 아키텍트 | Check |
| **QC 본부** | quality-gate, gap-analysis, completion-report, pdca-iteration | 품질 검증관, 갭 디텍터, 리포트 제너레이터, PDCA 이터레이터 | All/Check/Act |
| **태스크** | format-conversion | 포맷 컨버터 | All |

### Layer 2: Claude Universal Skills (19개)

**위치**: `.claude/skills/` 폴더
**목적**: 범용 유틸리티 스킬 (크로스 프로젝트 사용 가능)

#### 문서 생성 (6개)

| 스킬 | 설명 |
|------|------|
| **pptx** | PowerPoint 슬라이드 덱 생성/편집 |
| **docx** | Word 문서 생성/편집 (TOC, 테이블, 이미지 포함) |
| **xlsx** | Excel 스프레드시트 생성/편집 |
| **pdf** | PDF 처리, 추출, 변환, 병합 |
| **doc-coauthoring** | 문서 공동 작성 워크플로우 |
| **executive-summary** | 임원 보고용 요약 보고서 작성 |
| **internal-comms** | 내부 공지/뉴스레터/상태 보고 |

#### 비주얼 & 디자인 (5개)

| 스킬 | 설명 |
|------|------|
| **theme-factory** | 10개 프리셋 테마 (Ocean Depths, Sunset Boulevard 등) |
| **canvas-design** | PNG/PDF 포스터·아트 생성 |
| **algorithmic-art** | p5.js 제너러티브 아트 |
| **slack-gif-creator** | Slack용 애니메이션 GIF 생성 |
| **brand-guidelines** | Anthropic 브랜드 스타일 (와키윌리 어댑터 기반) |

#### 웹 & 프론트엔드 (3개)

| 스킬 | 설명 |
|------|------|
| **frontend-design** | 웹 UI/컴포넌트/대시보드 |
| **web-artifacts-builder** | 멀티페이지 React 웹앱 |
| **webapp-testing** | Playwright 웹앱 테스트 자동화 |

#### 지식 구조화 (1개)

| 스킬 | 설명 |
|------|------|
| **json-canvas** | Obsidian 캔버스/마인드맵 생성 |

#### 개발 도구 (3개)

| 스킬 | 설명 |
|------|------|
| **mcp-builder** | MCP 서버 개발 가이드 |
| **skill-creator** | 신규 스킬 설계/개선 |
| **claude-api** | Claude API/Agent SDK |

### Layer 3: Adapters & Bridges

**위치**: `skills-universal/` 폴더
**목적**: FPOF 스킬과 유니버설 스킬의 연계 및 브랜드/모델 맞춤화

#### 어댑터 (2개)

| 어댑터 | 목적 | 특징 |
|----------|------|------|
| **llm-api-guide.md** | 모델 무관 LLM API 개발 가이드 | OpenAI, Claude, Gemini, Mistral, Ollama 지원<br>- Python/TypeScript SDK 선택 가이드<br>- Single Call/Workflow/Agent 아키텍처<br>- Thinking 파라미터 비교 |
| **brand-styler.md** | 와키윌리 브랜드 스타일 적용 가이드 | Primary: #FEF200, #000000, #FFFFFF<br>- Secondary: #68A8DB (시즌 악센트)<br>- 타이포: Bold grotesque (Display), Clean sans-serif (Body) |

#### 브릿지 (1개)

**fpof-universal-map.md** - 에이전시별 연계 맵

| 에이전시 | FPOF 스킬 | 연계 유니버설 스킬 |
|----------|-----------|-------------------|
| **전략기획실** | trend-research | executive-summary |
| | brand-strategy | pptx, json-canvas |
| | md-planning | xlsx |
| | line-sheet | xlsx |
| **크리에이티브 스튜디오** | moodboard | canvas-design, theme-factory |
| | design-spec | docx |
| | visual-generation | algorithmic-art |
| | (모든 산출물) | brand-styler |
| **프로덕트 랩** | techpack | docx, pdf |
| | costing-ve | xlsx |
| | qr-process | docx |
| **마케팅 쇼룸** | imc-strategy | pptx, executive-summary |
| | visual-content | canvas-design, frontend-design |
| | copywriting | doc-coauthoring, internal-comms |
| | social-viral | slack-gif-creator |
| | (캠페인 산출물) | brand-styler |
| **데이터 인텔리전스** | sales-analysis | xlsx, executive-summary |
| | insight-archiving | pptx, json-canvas |
| **QC 본부** | gap-analysis | executive-summary, docx |
| | completion-report | pptx, pdf |
| | pdca-iteration | internal-comms |
| | quality-gate | xlsx |

---

## 🚀 사용법

### 자연어 요청

FPOF는 자연어 요청을 자동으로 적합한 스킬로 라우팅합니다.

**예시**:
```
"26SS 트렌드 분석해줘"
  → 전략기획실 > 시장 리서처 > trend-research 스킬 실행

"무드보드 만들어줘"
  → 크리에이티브 스튜디오 > 크리에이티브 디렉터 > moodboard 스킬 실행
```

### 슬래시 명령어

자주 사용하는 작업은 슬래시 명령어로 빠르게 실행할 수 있습니다.

**예시**:
```
/status       # 현재 상태 확인
/brief trend  # 트렌드 브리프 생성
/deck season  # 시즌 프레젠테이션 생성
```

### 범용 유틸리티 스킬

FPOF 패션 실무 외에 일반적인 문서 생성/디자인 작업도 가능합니다.

**예시**:
```
"PPT 덱 만들어줘"
  → pptx 스킬 실행 (범용)

"임원 보고서 요약해줘"
  → executive-summary 스킬 실행 (범용)
```

---

## 🔄 PDCA 워크플로우

### 전체 사이클

```
Plan (기획)
  ↓
  1. trend-research (트렌드 리서치)
  2. brand-strategy (브랜드 전략)
  3. md-planning (MD 전략)
  4. line-sheet (라인시트)
  ↓
  Quality Gate 1 (QG1)
  ↓
Design (디자인)
  ↓
  1. moodboard (무드보드)
  2. design-spec (디자인 스펙)
  3. costing-ve (원가 계산 & VE)
  4. visual-generation (AI 비주얼 생성)
  ↓
  Quality Gate 2 (QG2)
  ↓
Do (실행)
  ↓
  1. techpack (테크팩)
  2. imc-strategy (IMC 전략)
  3. visual-content (비주얼 콘텐츠)
  4. copywriting (카피라이팅)
  5. social-viral (소셜 & 바이럴)
  ↓
  Quality Gate 3 (QG3)
  ↓
Check (분석)
  ↓
  1. sales-analysis (매출 분석)
  2. insight-archiving (인사이트 아카이빙)
  3. gap-analysis (갭 분석)
  4. completion-report (완료 리포트)
  ↓
  Quality Gate 4 (QG4)
  ↓
Act (개선)
  ↓
  pdca-iteration (Match Rate < 90% 시 자동 개선)
```

### 품질 게이트 (QG)

| 게이트 | 기준 | 통과 조건 |
|-------|------|----------|
| **QG1** | Plan → Design 전환 | 6개 항목 PASS (트렌드 브리프, 브랜드 전략, MD 전략, 라인시트, 경영목표 정합성, 사용자 승인) |
| **QG2** | Design → Do 전환 | 6개 항목 PASS (무드보드, 디자인 스펙, 원가 검증, 디자인-기획 정합성, 비주얼 에셋, 사용자 승인) |
| **QG3** | Do → Check 전환 | 6개 항목 PASS (테크팩, 캠페인 브리프, 콘텐츠 기획서, 카피 데크, 런칭 시퀀스, 사용자 승인) |
| **QG4** | Check → Next Cycle | Match Rate ≥ 90% → COMPLETE<br>Match Rate < 90% → Act 단계 |

---

## 📚 스킬 전체 목록

### FPOF Main Skills (21개)

| 스킬 ID | 이름 | 에이전시 | 역할 | PDCA 단계 | 설명 |
|----------|------|----------|------|----------|
| **trend-research** | 트렌드 리서치 | 전략기획실 | 시장 리서처 | 글로벌/로컬 트렌드, 경쟁사 동향, 소비자 시그널 분석 |
| **brand-strategy** | 브랜드 전략 수립 | 전략기획실 | 브랜드 전략가 | 시즌 테마, 포지셔닝, 경영목표 연결, IP 활용 방향 |
| **md-planning** | MD 전략 & 시즌 컨셉 | 전략기획실 | 수석 MD | 카테고리 믹스, 가격 전략, 챔피언 상품, QR 계획 |
| **line-sheet** | 라인시트 작성 | 전략기획실 | 컬렉션 플래너 | SKU 리스트, OTB, 사이즈/컬러 브레이크다운 |
| **moodboard** | 무드보드 제작 | 크리에이티브 스튜디오 | 크리에이티브 디렉터 | 비주얼 키워드, 컬러 팔레트, 텍스처/소재 무드 |
| **design-spec** | 디자인 스펙 작성 | 크리에이티브 스튜디오 | 패션 디자이너 | 실루엣 & 디테일, 소재 & 컬러, 그래픽/프린트 |
| **visual-generation** | AI 비주얼 생성 | 크리에이티브 스튜디오 | 아트 디렉터 | 플랫 이미지, 룩북, 디테일, 캠페인, 배너 |
| **costing-ve** | 원가 계산 & VE | 프로덕트 랩 | 프로덕션 매니저 | 소재비/부자재비/가공비, 원가 합계, VE 제안 |
| **techpack** | 테크팩 작성 | 프로덕트 랩 | 프로덕션 매니저 | 8대 섹션: 기본 정보, 도식화, BOM, 사이즈 스펙 |
| **qr-process** | QR 프로세스 (리오더/SPOT) | 프로덕트 랩 | 프로덕션 매니저 | 호조상품 리오더, SPOT 트렌드 상품 단기 생산 |
| **imc-strategy** | IMC 전략 & GTM | 마케팅 쇼룸 | 마케팅 디렉터 | 캠페인 3단계(TEASING → MAIN → SUSTAIN), 채널 믹스 |
| **visual-content** | 비주얼 콘텐츠 기획 | 마케팅 쇼룸 | 콘텐츠 디렉터 | 화보 촬영 기획, 영상 콘텐츠, 채널별 에셋 |
| **copywriting** | 카피라이팅 & 스토리텔링 | 마케팅 쇼룸 | 패션 에디터 | PDP 카피, SNS 채널별 카피, 스토리텔링 |
| **social-viral** | 소셜 & 바이럴 전략 | 마케팅 쇼룸 | 소셜 전략 디렉터 | 인플루언서 매핑, 시딩 전략, 바이럴 메커니즘 |
| **sales-analysis** | 매출 분석 & KPI | 데이터 인텔리전스 | 트렌드 애널리스트 | 채널별/카테고리별 분석, 히트상품 분석, KPI 대시보드 |
| **insight-archiving** | 인사이트 도출 & 아카이빙 | 데이터 인텔리전스 | 인사이트 아키텍트 | 성공/실패 사례 분석, 인사이트 카드, 플레이북 |
| **quality-gate** | 품질 게이트 (QG1~QG4) | QC 본부 | 품질 검증관 | 각 단계 산출물 완전성과 정합성 검증 |
| **gap-analysis** | 갭 분석 | QC 본부 | 갭 디텍터 | 기획 vs 실적 비교, Match Rate 산출, 개선 액션 |
| **completion-report** | PDCA 완료 보고서 | QC 본부 | 리포트 제너레이터 | PDCA 사이클 요약, 성과, KPI, 다음 시즌 추천 |
| **pdca-iteration** | PDCA 자동 개선 | QC 본부 | PDCA 이터레이터 | Match Rate < 90% 시 자동 개선 루프 (최대 5회) |
| **format-conversion** | 문서 포맷 변환 | 태스크 | 포맷 컨버터 | DOCX/PPTX/XLSX/PDF 변환 |

### Claude Universal Skills (19개)

| 스킬 | 카테고리 | 설명 | 파일 크기 |
|------|----------|------|----------|
| **pptx** | 문서 생성 | PowerPoint 슬라이드 덱 생성/편집 | ~60줄 |
| **docx** | 문서 생성 | Word 문서 생성/편집 (TOC, 테이블, 이미지) | ~590줄 (가장 상세) |
| **xlsx** | 문서 생성 | Excel 스프레드시트 생성/편집 | ~80줄 |
| **pdf** | 문서 생성 | PDF 처리/추출/변환/병합 | ~120줄 |
| **doc-coauthoring** | 문서 생성 | 문서 공동 작성 워크플로우 | ~110줄 |
| **executive-summary** | 문서 생성 | 임원 보고용 요약 보고서 작성 | ~100줄 |
| **internal-comms** | 문서 생성 | 내부 공지/뉴스레터/상태 보고 | ~90줄 |
| **theme-factory** | 비주얼 & 디자인 | 10개 프리셋 테마 + 커스텀 | - |
| **canvas-design** | 비주얼 & 디자인 | PNG/PDF 포스터·아트 생성 | - |
| **algorithmic-art** | 비주얼 & 디자인 | p5.js 제너러티브 아트 | - |
| **slack-gif-creator** | 비주얼 & 디자인 | Slack용 애니메이션 GIF 생성 | - |
| **brand-guidelines** | 비주얼 & 디자인 | Anthropic 브랜드 스타일 (와키윌리 어댑터 기반) | - |
| **frontend-design** | 웹 & 프론트엔드 | 웹 UI/컴포넌트/대시보드 | - |
| **web-artifacts-builder** | 웹 & 프론트엔드 | 멀티페이지 React 웹앱 | - |
| **webapp-testing** | 웹 & 프론트엔드 | Playwright 웹앱 테스트 자동화 | - |
| **json-canvas** | 지식 구조화 | Obsidian 캔버스/마인드맵 생성 | - |
| **mcp-builder** | 개발 도구 | MCP 서버 개발 가이드 | - |
| **skill-creator** | 개발 도구 | 신규 스킬 설계/개선 | - |
| **claude-api** | 개발 도구 | Claude API/Agent SDK | - |

---

## 🎮 명령어 가이드

### 전체 명령어 (10개)

| 명령어 | 기능 | 설명 |
|--------|------|------|
| `/status` | 현재 상태 확인 | 시즌, PDCA 단계, QG 상태, 산출물 현황 |
| `/brief [유형]` | 산출물 작성 | 현재 PDCA 단계에서 다음 산출물 자동 생성 |
| `/deck [유형]` | 프레젠테이션 생성 | trend/season/moodboard/lookbook/campaign/report |
| `/pdf [유형]` | PDF 보고서 생성 | trend-report/season-book/techpack/campaign-brief/season-report/kpi-dashboard |
| `/sheet [유형]` | 엑셀 시트 생성 | line-sheet/otb/category-mix/cost-estimate/color-size/bom/production/marketing-budget/sales-data/kpi-tracker |
| `/doc [유형]` | 워드 문서 생성 | trend-brief/season-plan/brand-brief/design-brief/design-review/production-spec/campaign-plan/press-release/pdp-copy/season-review/playbook |
| `/export [detail]` | 산출물 목록 정리 | 모든 산출물 요약 |
| `/next` | 다음 단계 전환 | PDCA 다음 단계로 (QG 포함) |
| `/review` | 품질 검수 | 현재 단계 QG 실행 |
| `/team` | 팀 구성 조회 | 6개 에이전시, 20명 팀원 현황 |

---

## 📁 폴더 구조

```
FPOF V2.0/
├── README.md                        # 이 파일
├── CLAUDE.md                        # 시스템 기본 설정
├── .fpof-state.json                # 현재 시즌/PDCA 상태
├── .gitignore
│
├── .claude/                         # Claude 훅 & 스킬 설정
│   ├── hooks.json                  # 훅 설정
│   ├── hooks/
│   │   ├── route-skill.sh         # 자연어 → 스킬 라우팅
│   │   └── check-output.sh        # 산출물 검수 체크리스트
│   ├── commands/                  # 슬래시 명령어 (10개)
│   │   ├── status.md
│   │   ├── brief.md
│   │   ├── deck.md
│   │   ├── pdf.md
│   │   ├── sheet.md
│   │   ├── doc.md
│   │   ├── export.md
│   │   ├── next.md
│   │   ├── review.md
│   │   └── team.md
│   └── skills/                    # Claude 유니버설 스킬 (19개)
│       ├── pptx/
│       ├── docx/
│       ├── xlsx/
│       ├── pdf/
│       ├── doc-coauthoring/
│       ├── executive-summary/
│       ├── internal-comms/
│       ├── theme-factory/
│       │   └── themes/           # 10개 프리셋
│       ├── canvas-design/
│       ├── algorithmic-art/
│       ├── slack-gif-creator/
│       ├── brand-guidelines/
│       ├── frontend-design/
│       ├── web-artifacts-builder/
│       ├── webapp-testing/
│       ├── json-canvas/
│       ├── mcp-builder/
│       ├── skill-creator/
│       └── claude-api/
│
├── skills/                          # FPOF 메인 스킬 (21개)
│   ├── strategy/                   # 전략기획실 (4개)
│   │   ├── trend-research.md
│   │   ├── brand-strategy.md
│   │   ├── md-planning.md
│   │   └── line-sheet.md
│   ├── creative/                   # 크리에이티브 스튜디오 (3개)
│   │   ├── moodboard.md
│   │   ├── design-spec.md
│   │   └── visual-generation.md
│   ├── product/                    # 프로덕트 랩 (3개)
│   │   ├── costing-ve.md
│   │   ├── techpack.md
│   │   └── qr-process.md
│   ├── marketing/                  # 마케팅 쇼룸 (4개)
│   │   ├── imc-strategy.md
│   │   ├── visual-content.md
│   │   ├── copywriting.md
│   │   └── social-viral.md
│   ├── data/                       # 데이터 인텔리전스 (2개)
│   │   ├── sales-analysis.md
│   │   └── insight-archiving.md
│   ├── quality/                    # QC 본부 (4개)
│   │   ├── quality-gate.md
│   │   ├── gap-analysis.md
│   │   ├── completion-report.md
│   │   └── pdca-iteration.md
│   └── task/                      # 태스크 (1개)
│       └── format-conversion.md
│
├── skills-universal/               # 유니버설 어댑터 & 브릿지
│   ├── README.md                  # 마스터 인덱스
│   ├── nl-triggers.md             # 자연어 → 유니버설 스킬 매핑
│   ├── adapters/                  # 어댑터 (2개)
│   │   ├── llm-api-guide.md
│   │   └── brand-styler.md
│   └── bridges/                   # 브릿지 (1개)
│       └── fpof-universal-map.md   # 에이전시별 연계 맵
│
├── presets/                        # 와키윌리 브랜드 프리셋 (7개)
│   └── wacky-willy/
│       ├── brand.config.json       # 브랜드 DNA, 비전, 5대 경영목표
│       ├── personas.json           # UNI/WOMAN 페르소나
│       ├── tone-manner.json        # 톤앤매너, 브랜드 어휘
│       ├── visual-identity.json     # 컬러, 타이포, 그래픽 스타일
│       ├── categories.json         # 카테고리, 상품 전략
│       ├── channels.json            # 6개 채널 매출/목표
│       └── ip-bible.json           # 키키+11 캐릭터, 그룹, 관계도
│
├── docs/                           # 문서
│   ├── user-manual.md
│   ├── quickstart-guide.md
│   ├── wacky-willy-user-manual.md
│   ├── wacky-willy-presentation.md
│   └── reference/                # 참고 자료
│       ├── fpof-architecture.md
│       ├── brand-strategy.md
│       └── ...
│
├── knowledge/                       # 지식 베이스
│   └── index.md
│
├── output/                          # 산출물 저장
│   ├── [시즌]/
│   │   ├── _season/              # 시즌 전체 문서
│   │   └── [프로젝트]/           # 아이템 프로젝트
│   ├── meeting/                   # 회의 산출물
│   └── weekly review/            # 주간 리뷰
│
└── converter/                       # 문서 변환 시스템
    ├── config/
    ├── core/
    ├── generators/
    └── themes/
```

---

## 📌 요약 통계

| 항목 | 수량 |
|------|------|
| **FPOF 메인 스킬** | 21개 |
| **Claude 유니버설 스킬** | 19개 |
| **어댑터** | 2개 |
| **브릿지** | 1개 |
| **슬래시 명령어** | 10개 |
| **브랜드 프리셋** | 7개 |
| **에이전시** | 6개 |
| **팀원 역할** | 20개 |
| **총 스킬** | 40개 |

---

## 🚀 빠른 시작

### 1단계: 현재 상태 확인

```
/status
```

### 2단계: 작업 시작

자연어로 요청하거나 슬래시 명령어를 사용하세요.

**예시**:
```
"26SS 트렌드 분석해줘"
/deck season
/brief trend
```

### 3단계: 품질 검수

각 단계 완료 시 자동으로 검수가 실행됩니다. 수동으로 검수도 가능합니다.

```
/review
```

### 4단계: 다음 단계

현재 단계의 모든 산출물이 완료되면 다음 단계로 넘어갈 수 있습니다.

```
/next
```

---

## 📖 추가 참고자료

- [CLAUDE.md](./CLAUDE.md) — FPOF 와키윌리 시스템 상세 설정
- [docs/quickstart-guide.md](./docs/quickstart-guide.md) — 5분 퀵스타트 가이드
- [docs/user-manual.md](./docs/user-manual.md) — 전체 사용자 매뉴얼
- [skills-universal/README.md](./skills-universal/README.md) — 유니버설 스킬 상세 가이드

---

## 📞 지원

FPOF 시스템 사용 중 문제가 있거나 기능 개선 제안이 있으시면 문의해 주세요.

---

**버전**: 1.0.0
**최종 업데이트**: 2026-03-05
**라이선스**: Copyright © 2026 Wacky Willy. All rights reserved.
