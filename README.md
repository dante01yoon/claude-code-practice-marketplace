# claude-code-practice-marketplace

팀에서 함께 쓰는 Claude Code 플러그인 마켓플레이스입니다.

## 플러그인

| 이름 | 설명 |
| --- | --- |
| [web-kit](plugins/web-kit) | 요구사항 체크리스트로 `index.html` 웹 페이지를 만들고(`web-page` 스킬), Playwright로 데스크톱·모바일 화면을 확인(`screen-checker` 에이전트) |
| [starter-setting](plugins/starter-setting) | 새 프로젝트용 스타터 세팅: `web-page`·`seoul-data`·`setup` 스킬, `reviewer`·`screen-checker` 에이전트, 위험 명령 차단·모델 변경 확인·Prettier 훅, context7·playwright MCP, 프롬프트 위 개수 표시 |

## 설치

Claude Code에서:

```
/plugin marketplace add dante01yoon/claude-code-practice-marketplace
/plugin install web-kit@claude-code-practice-marketplace
/plugin install starter-setting@claude-code-practice-marketplace
```

## 팀 프로젝트에 자동 등록

프로젝트의 `.claude/settings.json`에 아래를 넣으면, 팀원이 그 폴더를 신뢰할 때 마켓플레이스 추가와 플러그인 설치를 안내받습니다.

```json
{
  "extraKnownMarketplaces": {
    "claude-code-practice-marketplace": {
      "source": {
        "source": "github",
        "repo": "dante01yoon/claude-code-practice-marketplace"
      }
    }
  },
  "enabledPlugins": {
    "web-kit@claude-code-practice-marketplace": true
  }
}
```

## 업데이트

```
/plugin marketplace update claude-code-practice-marketplace
```

## web-kit 요구 사항

- Node.js (`npx`로 `@playwright/mcp`를 실행)
- 인터넷 연결 (context7 MCP 사용)

## starter-setting 요구 사항

- `jq` (훅, 상태줄), Node.js (`npx`: Playwright MCP, Prettier 훅), Python 3 (`seoul-data` 스킬)
- 설치 후 프로젝트에서 `/starter-setting:setup`을 실행하면 CLAUDE.md, .gitignore, 상태줄·권한이 들어갑니다.
