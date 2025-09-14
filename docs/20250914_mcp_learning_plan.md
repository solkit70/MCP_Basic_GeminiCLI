# MCP(Model-Centric Programming) 학습 계획

AI 애플리케이션 개발자로서 Gemini CLI를 사용하여 MCP를 마스터하기 위한 학습 계획입니다.

## 1단계: MCP 소개

### 목표
*   MCP의 핵심 개념과 AI 개발에서의 이점을 이해합니다.
*   MCP가 최신 개발 워크플로우에 어떻게 부합하는지 파악합니다.

### 개념
MCP(Model-Centric Programming)는 소프트웨어 개발의 중심에 '모델'을 두는 패러다임입니다. 여기서 모델은 데이터 구조, 비즈니스 로직, AI 모델 등 애플리케이션의 핵심 요소를 정의합니다. 개발자는 모델을 중심으로 코드를 생성하고, 상호작용하며, 애플리케이션을 구축합니다. 이를 통해 코드의 일관성을 유지하고, 개발 생산성을 높이며, 유지보수를 용이하게 합니다.

### Gemini CLI를 사용한 개념 확인 (가상 예제)
MCP의 개념을 이해하기 위해, 가상의 `mcp` CLI 도구가 있다고 상상해 보겠습니다.

1.  **MCP 정보 확인:**
    ```bash
    mcp --version
    mcp --help
    ```

2.  **MCP 핵심 개념 설명 요청:**
    (Gemini CLI에게 질문)
    "MCP의 '모델'이란 무엇인가요? 기존의 MVC 패턴과 어떻게 다른가요?"

## 2단계: MCP 클라이언트 사용법

### 목표
*   MCP 클라이언트 환경을 설정하고 기본 명령어를 익힙니다.
*   MCP 서버에서 모델을 가져오고 사용하는 방법을 실습합니다.

### 설정 및 기본 명령어
1.  **MCP 클라이언트 설치 (가상):**
    ```bash
    # (가상) pip install mcp-cli
    ```

2.  **서버 연결 설정:**
    ```bash
    # (가상) mcp config set server public.mcp.server.com
    ```

### Gemini CLI를 사용한 실습 예제
1.  **서버의 모델 목록 확인:**
    ```bash
    # (가상) mcp model list
    ```
    *출력 예시:*
    ```
    - text/summarizer
    - image/classifier
    - translation/eng-to-kor
    ```

2.  **특정 모델의 정보 확인:**
    ```bash
    # (가상) mcp model info text/summarizer
    ```
    *출력 예시:*
    ```
    Model: text/summarizer
    Description: 긴 텍스트를 요약하는 모델입니다.
    Input: string
    Output: string
    ```

3.  **모델 사용해보기:**
    ```bash
    # (가상) mcp model run text/summarizer --input "..."
    ```

## 3단계: MCP 서버 작업

### 목표
*   기존 MCP 서버에 연결하고 모델을 활용합니다.
*   MCP 모델을 사용하여 간단한 AI 애플리케이션을 개발합니다.

### Gemini CLI를 사용한 애플리케이션 개발 예제
간단한 텍스트 요약 애플리케이션을 만들어 보겠습니다.

1.  **프로젝트 폴더 생성:**
    ```bash
    mkdir mcp-summary-app
    cd mcp-summary-app
    ```

2.  **애플리케이션 코드 작성 (예: `app.py`):**
    Gemini CLI를 사용하여 `app.py` 파일을 생성합니다.
    ```python
    import os
    import sys

    def summarize_text(text):
        # In a real scenario, this would call the MCP client
        # For this example, we simulate the call
        print(f"MCP-CLI: Simulating call to 'text/summarizer' with input: {text}")
        # Simulated output
        return f"요약 결과: {text[:20]}..."

    if __name__ == "__main__":
        input_text = sys.argv[1]
        summary = summarize_text(input_text)
        print(summary)
    ```

3.  **애플리케이션 실행:**
    ```bash
    python app.py "MCP는 모델 중심 프로그래밍입니다..."
    ```

## 4단계: MCP 서버 생성 및 게시

### 목표
*   사용자 정의 MCP 모델을 설계하고 생성합니다.
*   모델을 호스팅하기 위한 간단한 MCP 서버를 구축하고 게시합니다.

### Gemini CLI를 사용한 서버 구축 예제
"인사말 생성기" 모델을 만들어 보겠습니다.

1.  **모델 정의 파일 생성 (`greeting.mcp.yaml`):**
    Gemini CLI를 사용하여 `greeting.mcp.yaml` 파일을 생성합니다.
    ```yaml
    model: custom/greeting
    description: "사용자 이름으로 인사말을 생성합니다."
    version: 1.0.0
    input:
      type: object
      properties:
        name:
          type: string
    output:
      type: string
    ```

2.  **모델 구현 코드 작성 (`handler.py`):**
    ```python
    def handle(input):
        name = input.get("name", "Guest")
        return f"안녕하세요, {name}님!"
    ```

3.  **MCP 서버 설정 (`server.mcp.yaml`):**
    ```yaml
    server:
      host: 0.0.0.0
      port: 8080
    models:
      - path: ./greeting.mcp.yaml
        handler: handler.handle
    ```

4.  **서버 실행 (가상):**
    ```bash
    # (가상) mcp server start
    ```

5.  **서버 게시 (가상):**
    ```bash
    # (가상) mcp server publish --name my-greeting-server
    ```

### 다음 단계
이 학습 계획을 바탕으로 각 단계별 실습을 진행하며 MCP에 대한 이해를 심화시킬 수 있습니다. 각 단계에서 궁금한 점이 생기면 언제든지 Gemini CLI에 질문하여 도움을 받으세요.