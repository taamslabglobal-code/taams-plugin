# TAAMs — 한국 수입식품 데이터 플러그인

한국 **식품의약품안전처(MFDS) 통관 데이터**를 Claude 안에서 바로 조회한다.
수입단가·통관실적·수입사/수출사·국내 도매경매 낙찰가·산지 기상까지 **조회 전용** 도구 19종.

> 설치되는 서버 프로세스는 없다. 이 플러그인은 **원격 MCP 서버**(`mcp.taamsglobal.com`)를
> 가리키는 설정과 리포트 스킬만 담는다.

## 설치

```bash
claude plugin marketplace add taamslabglobal-code/taams-plugin
claude plugin install taams@taams
```

처음 도구를 부를 때 브라우저로 로그인 창이 열린다(OAuth). TAAMs 계정이 없으면
그 화면에서 가입할 수 있다. 계정·등급별 이용 범위는 **<https://taamsglobal.com/mcp-guide>** 참조.

## 무엇을 물을 수 있나

```
망고 수입단가 최근 추이 보여줘
새우 수입사 중 물량 상위는 어디야
당근 도매경매 낙찰가를 시장별로 비교해줘
/taams:report 아보카도
```

`/taams:report [품목명]` 은 단가·수입량·산지 기상을 한 리포트로 묶어 준다.

## 알아 둘 것

- **통관 데이터는 약 3일 지연 공개**된다. 최근 며칠이 비어 보이는 것은 정상이다.
- **수입단가는 통관 금액 ÷ 중량으로 얻은 값(USD/kg)** 이라 실제 거래가와 다를 수 있다.
- 수입사 연락처 등 일부 상세는 **등급·권한에 따라 제공되지 않는다.** 값이 없는 것과
  권한이 없는 것은 다르며, 후자면 응답에 안내가 함께 온다.
- 산지 기상과 단가는 **나란히 놓인 사실일 뿐 인과가 아니다.** 도구들은 인과로 엮지
  않도록 지시받는다.

## 접속 대상 바꾸기

기본값은 운영 서버다. 다른 엔드포인트로 붙일 때만 환경변수를 준다.

```bash
TAAMS_MCP_URL=http://127.0.0.1:8003/mcp claude
```

---

## In English

TAAMs brings **Korean food-import customs data (MFDS)** into Claude — import prices,
customs records, importer/exporter profiles, domestic wholesale auction prices, and
origin weather. **19 read-only tools**, served by a remote MCP server; nothing runs locally.

Ask in English or Korean — product search accepts either. See
<https://taamsglobal.com/mcp-guide> for accounts, grades, and rate limits.

---

문의 support@taamsglobal.com · 탬스글로벌 · <https://taamsglobal.com>
