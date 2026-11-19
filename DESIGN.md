# Tarot (오늘의 타로) — Design System Guide (DESIGN.md)
> Modern Editorial Mystic — 담백하고 정제된 연구실의 기록 노트 위에 피어난 모던 타로.

**Theme:** Light (Mobile-First Web)  
**Target:** 20대 대학생 및 사회초년생  
**Core Principles:** 무설치 · 1분 내 완료 · 데이터 즉시 폐기(Zero Retention) · 미니멀 타이포그래피

---

## 1. 개요 및 디자인 철학

OpenAI의 절제된 타이포그래피 기반 에디토리얼 캔버스 철학을 계승하여, 기존 점술/타로 서비스 특유의 원색적이고 복잡한 그래픽을 걷어내고 **순백의 종이(Paper)와 단정한 먹(Obsidian), 그리고 섬세한 헤어라인(Hairline)** 중심의 모던 미니멀리즘을 구축합니다.

- **절제된 시각 언어**: 페이지 전반에서 색상의 남용을 엄격히 금지합니다. 유일하게 채워진(Filled) 시각적 강조점은 핵심 전환 버튼([타로 시작], [카드 한 장 뽑기])뿐이며, 이는 문장의 마침표처럼 기능합니다.
- **모바일 최적화 (Max-Width 440px)**: 한 손 조작에 최적화된 모바일 중심 뷰포트 레이아웃을 제공하며, 데스크톱 환경에서는 중앙 집중식 카드 프레임으로 렌더링됩니다.
- **신뢰와 안도감**: 12% 투명도의 섬세한 헤어라인 보더와 명확한 `Alert` 콜아웃 컴포넌트를 통해 "입력한 개인정보는 서버로 전송되지 않고 즉시 폐기된다"는 메시지를 안정감 있게 전달합니다.
- **1080×1350 인스타 스토리 비율**: 결과 화면 카드는 소셜 미디어 및 메신저 공유에 최적화된 세로형 비율(4:5 / 1080×1350)과 넉넉한 여백의 완성도 높은 레이아웃을 갖춥니다.

---

## 2. 디자인 토큰 (Design Tokens)

### 2.1 Colors (색상)

| Name | Hex / Alpha | Token | shadcn Semantic | Role |
|------|-------------|-------|-----------------|------|
| **Obsidian** | `#09090b` | `--color-obsidian` | `--foreground`, `--primary` | 본문 텍스트, Primary CTA 버튼 배경, 강력한 시각적 중심 |
| **Primary Active** | `#27272a` | `--color-primary-active` | `--primary-active` | Primary 버튼 호버 및 누름 상태 |
| **Graphite** | `#52525b` | `--color-graphite` | `--muted-foreground` | 서브 레이블, 헬퍼 텍스트, 날짜/별자리 보조 정보 |
| **Smoke** | `#a1a1aa` | `--color-smoke` | `--muted-foreground/60` | 플레이스홀더, 비활성 텍스트, 카드 뒷면 보조 라인 |
| **Paper** | `#ffffff` | `--color-paper` | `--background`, `--card`, `--popover` | 기본 배경 캔버스, 결과 카드 표면 |
| **Ash** | `#f4f4f5` | `--color-ash` | `--muted`, `--secondary` | 토글 칩 선택 상태, 약한 면 분할, 호버 표면 |
| **Hairline** | `rgba(0, 0, 0, 0.08)` | `--color-hairline` | `--border`, `--input` | 모든 구분선, 인풋 및 아웃라인 버튼 테두리 |
| **Hairline Dark** | `rgba(0, 0, 0, 0.16)` | `--color-hairline-dark` | `--ring` | 포커스 링, 선택된 토글 버튼 테두리 |
| **Mystic Whisper** | `rgba(99, 102, 241, 0.06)` | `--color-mystic-whisper` | `--accent` | 개인정보 안내 콜아웃 배경, 타로 카드 뒷면 미세 음영 |
| **Destructive** | `#ef4444` | `--color-destructive` | `--destructive` | 생년월일 유효성 오류 피드백 |

---

### 2.2 Typography (타이포그래피)

가독성과 현대적인 인쇄물 느낌을 주는 **Pretendard** (또는 Inter / 시스템 산세리프)를 기본 서체로 적용하며, 타로 카드의 신비로움과 상징성을 위해 카드 명칭 표기 시 세리프(Cinzel, Noto Serif KR)를 포인트 서체로 보조 활용합니다.

- **Primary Font Family:** `Pretendard, -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif`
- **Mystic Serif (Accent for Card Title):** `'Cinzel', 'Noto Serif KR', serif`

#### Type Scale

| Role | Size | Weight | Line Height | Tracking | Token | Tailwind Class |
|------|------|--------|-------------|----------|-------|----------------|
| **Display** | 36px | 600 (Semibold) | 1.15 | -0.03em | `--text-display` | `text-4xl font-semibold tracking-tight` |
| **Title / Heading** | 24px | 600 (Semibold) | 1.25 | -0.02em | `--text-heading` | `text-2xl font-semibold tracking-tight` |
| **Subheading** | 18px | 500 (Medium) | 1.35 | -0.015em | `--text-subheading` | `text-lg font-medium` |
| **Body (해석 본문)** | 15px | 400 (Regular) | 1.65 | -0.01em | `--text-body` | `text-[15px] font-normal leading-relaxed` |
| **Input / Label** | 14px | 500 (Medium) | 1.4 | -0.01em | `--text-label` | `text-sm font-medium` |
| **Caption / Notice** | 12px | 400 (Regular) | 1.5 | 0 | `--text-caption` | `text-xs text-muted-foreground` |

---

### 2.3 Spacing & Shapes (간격 및 라운드)

**Base Unit:** 4px  
**Layout Container:** 모바일 뷰포트 `max-w-[440px]`, 좌우 패딩 `px-5 (20px)`

#### Spacing Scale
- `gap-2` (8px): 칩 간격, 인풋과 레이블 간격
- `gap-3` (12px): 폼 필드 내부 요소 간격
- `gap-4` (16px): 결과 화면 카드 내부 섹션 간격
- `gap-6` (24px): 폼 필드 그룹 간격 (`FieldGroup`)
- `py-8` ~ `py-10` (32px~40px): 화면 상하단 여백

#### Border Radius (`rounded-*`)
- **Buttons & Tags (알약 형태):** `rounded-full` (`9999px`) — OpenAI 및 모던 UI 시그니처
- **Inputs & Toggles:** `rounded-xl` (`12px`) 또는 `rounded-full` (`9999px`)
- **Tarot Card Frame:** `rounded-2xl` (`16px`) — 모바일 화면 속 단정한 카드 비율
- **Callout / Alert:** `rounded-xl` (`12px`)

#### Shadows & Elevation
- **기본 기조:** 무음영 (Flat Hairline). 섀도우를 배제하고 `1px border`와 면 분할로만 깊이를 형성.
- **Card Flip / Hover (미세 부유감):** `0 10px 30px -10px rgba(0,0,0,0.08)`

---

## 3. shadcn 컴포넌트 구성 규칙 (Rules & Recipes)

`shadcn/ui` 원칙을 철저히 준수하며, 원시 `div`를 스타일링하지 않고 시맨틱 컴포넌트를 조합합니다.

### 3.1 Button (버튼)
- **Primary CTA ([타로 시작], [카드 한 장 뽑기]):**
  - 형태: `size="lg"`, `className="w-full rounded-full bg-primary text-primary-foreground font-medium h-12 shadow-none hover:bg-zinc-800 transition-all"`
  - 시스템 내 유일하게 면이 채워진 마침표 버튼.
- **Secondary / Action ([이미지 저장], [결과 공유]):**
  - 형태: `variant="outline"`, `className="rounded-full border-border hover:bg-muted font-medium h-11"`
- **Utility ([다시 뽑기], [처음으로]):**
  - 형태: `variant="ghost"`, `className="rounded-full text-muted-foreground hover:text-foreground text-xs"`

### 3.2 Form & Input (정보 입력 — F-2)
- **구조:** 반드시 `FieldGroup` + `Field` + `FieldLabel` + `Input` 구성을 준수합니다 (`space-y-*` 금지).
```tsx
<FieldGroup className="flex flex-col gap-5">
  <Field className="flex flex-col gap-1.5">
    <FieldLabel htmlFor="name" className="text-xs font-medium text-foreground">
      이름 (닉네임 OK)
    </FieldLabel>
    <Input 
      id="name"
      maxLength={10}
      placeholder="지민" 
      className="h-11 rounded-full border-border px-4 text-sm focus-visible:ring-1 focus-visible:ring-foreground"
    />
  </Field>
</FieldGroup>
```

### 3.3 Topic Selector (주제 선택 6개 — F-2)
- 6개 선택지(커리어, 재물, 연애, 건강, 학업, 종합)는 `Button` 반복문이 아닌 `ToggleGroup` + `ToggleGroupItem`을 사용합니다.
- 레이아웃: 3열 2행 (`grid grid-cols-3 gap-2`).
- 비활성: `variant="outline"` 테두리, 활성: `bg-foreground text-background` 반전.

```tsx
<ToggleGroup type="single" value={topic} onValueChange={setTopic} className="grid grid-cols-3 gap-2">
  <ToggleGroupItem value="career" className="rounded-full border border-border h-10 text-xs font-medium data-[state=on]:bg-foreground data-[state=on]:text-background">
    💼 커리어
  </ToggleGroupItem>
  <ToggleGroupItem value="wealth" className="rounded-full border border-border h-10 text-xs font-medium data-[state=on]:bg-foreground data-[state=on]:text-background">
    💰 재물
  </ToggleGroupItem>
  {/* 연애, 건강, 학업, 종합 */}
</ToggleGroup>
```

### 3.4 Tarot Card & Result Frame (결과 카드 — F-4, F-5)
- 인스타 스토리 및 세로 이미지 다운로드(1080×1350)에 1:1로 대응하는 카드 컨테이너.
- 구성: `Card` + `CardHeader` + `CardContent` + `CardFooter`.
- 카드 내 요소:
  1. 헤더: `{이름}님의 타로 · {주제}` + 별자리 뱃지 (`Badge`)
  2. 중앙: 타로 카드 비주얼 (22장 메이저 아르카나, 부드러운 1초 뒤집기 트랜지션)
  3. 명칭: 로마 숫자 + 한글 명칭 (`XIX 태양 · ♌ 사자자리`)
  4. 본문: 3줄 90자 이내 맞춤 해석 (기본문장 + 별자리문장 + 전공문장)
  5. 푸터: `※ 오락용 타로 해석입니다` + 서비스 브랜딩 워터마크

```tsx
<div id="taro-capture-card" className="aspect-[4/5] w-full rounded-2xl border border-border bg-card p-6 flex flex-col justify-between text-center select-none">
  <div className="flex justify-between items-center text-xs text-muted-foreground">
    <span className="font-medium text-foreground">{name}님의 타로 · {topicName}</span>
    <Badge variant="outline" className="rounded-full font-normal text-[11px]">{zodiacSign}</Badge>
  </div>
  
  {/* 카드 일러스트 영역 (1초 뒤집기) */}
  <div className="py-3 flex justify-center">
    <div className="relative w-36 h-56 rounded-xl border border-border/80 overflow-hidden shadow-sm">
      <img src={cardImage} alt={cardName} className="w-full h-full object-cover" />
    </div>
  </div>

  <div className="flex flex-col gap-2">
    <h3 className="font-serif text-lg font-semibold tracking-wide text-foreground">
      {cardRoman} {cardName}
    </h3>
    <div className="text-[14px] leading-relaxed text-zinc-700 flex flex-col gap-0.5">
      <p>{line1}</p>
      <p>{line2}</p>
      {line3 && <p>{line3}</p>}
    </div>
  </div>

  <p className="text-[11px] text-muted-foreground/70">
    ※ 오락용 타로 해석입니다 · 오늘의 타로
  </p>
</div>
```

### 3.5 Privacy Callout (개인정보 안내문 — F-2, F-4)
- 불안감을 해소하기 위해 `Alert` 컴포넌트로 처리 (`div` 배경색 하드코딩 금지).
```tsx
<Alert className="rounded-xl border border-border/70 bg-zinc-50/70 p-3 text-xs text-muted-foreground flex items-center gap-2">
  <ShieldCheckIcon className="size-4 text-zinc-600 shrink-0" />
  <span>입력한 정보는 서버로 전송되지 않고 화면을 닫으면 즉시 삭제돼요.</span>
</Alert>
```

### 3.6 Toasts & Feedback (알림 — F-5, F-6)
- Base UI / Sonner 기반 `toast`:
  - 이미지 저장 성공: `"이미지를 저장했어요"`
  - 클립보드 복사 완료: `"결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요"`

---

## 4. 화면별 레이아웃 가이드 (Screen Workflows)

### S-01 시작 화면 (F-1)
- **구성:**
  - 중앙 상단: 브랜드 아이콘 및 타이틀 (`🔮 오늘의 타로`)
  - 중앙: 신비로운 카드 뒷면 일러스트 (`aspect-[2/3] w-40`)
  - 헤드카피: `내 정보를 넣고 카드 한 장으로 나만의 해석을 받아 봐요`
  - 하단 CTA: `[타로 시작]` (Primary Black Pill Button)
  - 풋노트: `※ 오락용 타로 · 정보는 저장 안 해요`

### S-02 내 정보 & 주제 선택 화면 (F-2)
- **구성:**
  - 상단: 뒤로가기 버튼 + `나에 대해 알려 주세요` 헤더
  - 본문 폼:
    1. 이름 입력 (`maxLength={10}`, 닉네임 권장)
    2. 생년월일 입력 (`YYYY . MM . DD` 형태, 숫자 유효성 검증)
    3. 전공 입력 (선택 사항, 미입력 시 2줄 해석)
    4. 궁금한 주제 선택 (6구 토글 그룹)
  - 중간: `Alert` 개인정보 무저장 원칙 안내
  - 하단: `[카드 한 장 뽑기]` (이름 · 생년월일 · 주제 충족 시 활성화)

### S-03 맞춤 해석 결과 화면 (F-4 ~ F-7)
- **구성:**
  - 중앙: 1080×1350 캡처 대상 `Tarot Card` 뷰
  - 조작 버튼군 (2×2 배치 또는 세로 스택):
    - `[이미지 저장]` (Primary/Outline Button)
    - `[결과 공유]` (기기 공유 API 연동, 미지원 시 자동 복사)
    - `[다시 뽑기]` (기존 정보 유지한 채 S-02로 이동)
    - `[처음으로]` (모든 메모리 데이터 즉시 초기화 후 S-01로 이동)
  - 하단 고지: `🔒 정보는 저장되지 않아요. [처음으로]를 누르면 바로 지워져요.`

---

## 5. Do's and Don'ts (규칙)

### Do
- **Pill Radius 일관성**: 모든 인터랙티브 컨트롤(버튼, 태그 칩, 인풋)에 `rounded-full`을 우선 적용합니다.
- **헤어라인 테두리**: 회색 헥사코드(`#e5e7eb`) 대신 투명도가 있는 검정 `rgba(0, 0, 0, 0.08)`를 사용하여 배경과 자연스럽게 융화되도록 합니다.
- **3줄 90자 해석 절제**: 해석 텍스트는 3줄을 넘지 않으며, 문맥이 길어져 스크롤을 유발하지 않도록 글자 수를 철저히 통제합니다.
- **단정적 표현 배제**: "돈을 법니다", "질병이 낫습니다" 대신 "지출 우선순위를 돌아볼 때예요" 같은 조언형 문장만을 채택합니다.
- **클라이언트 전용 처리**: 생년월일로 별자리를 계산하고 문구를 매칭하는 모든 로직은 브라우저 메모리 안에서만 수행합니다.

### Don't
- **화려한 네온·그라데이션 금지**: 보라색·금색의 번쩍이는 운세 앱 클리셰를 배제하고, 무채색 인쇄물과 같은 진중함을 유지합니다.
- **생년월일 외부 노출 금지**: 결과 이미지 및 공유 문구에 절대 생년월일이나 전공 원문을 삽입하지 않습니다 (이름과 별자리만 노출).
- **불필요한 그림자 금지**: 입체감을 주는 묵직한 `box-shadow`를 지양하고 얇은 보더와 여백으로 계층을 만듭니다.
- **서버 API 호출 금지**: 개인정보 저장을 위한 엔드포인트나 외부 LLM 실시간 호출을 두지 않습니다 (원칙 1 준수).

---

## 6. CSS 코드 셋업 (Code Snippets)

### 6.1 Tailwind v4 `@theme` 설정 (`globals.css`)

```css
@import "tailwindcss";

@theme inline {
  /* Colors */
  --color-obsidian: #09090b;
  --color-graphite: #52525b;
  --color-smoke: #a1a1aa;
  --color-paper: #ffffff;
  --color-ash: #f4f4f5;
  --color-hairline: rgba(0, 0, 0, 0.08);
  --color-hairline-dark: rgba(0, 0, 0, 0.16);

  /* Radius Scale for shadcn */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  --radius-2xl: 20px;
  --radius-full: 9999px;

  /* Typography */
  --font-sans: 'Pretendard', -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;
  --font-serif: 'Cinzel', 'Noto Serif KR', serif;
}

:root {
  /* shadcn semantic tokens */
  --background: #ffffff;
  --foreground: #09090b;

  --card: #ffffff;
  --card-foreground: #09090b;

  --popover: #ffffff;
  --popover-foreground: #09090b;

  --primary: #09090b;
  --primary-foreground: #ffffff;
  --primary-active: #27272a;

  --secondary: #f4f4f5;
  --secondary-foreground: #18181b;

  --muted: #f4f4f5;
  --muted-foreground: #71717a;

  --accent: #f4f4f5;
  --accent-foreground: #18181b;

  --destructive: #ef4444;
  --destructive-foreground: #ffffff;

  --border: rgba(0, 0, 0, 0.08);
  --input: rgba(0, 0, 0, 0.08);
  --ring: #09090b;

  --radius: 0.75rem;
}
```

### 6.2 카드 뒤집기 CSS 애니메이션 (1초 이내 뒤집기)

```css
.card-flip-container {
  perspective: 1000px;
}

.card-flip-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
  transform-style: preserve-3d;
}

.card-flip-inner.is-flipped {
  transform: rotateY(180deg);
}

.card-face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
}

.card-face-back {
  transform: rotateY(180deg);
}
```
