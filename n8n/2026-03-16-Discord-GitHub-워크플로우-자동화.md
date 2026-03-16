### Context
n8n을 사용한 첫 번째 자동화 워크플로우는 Discord에서 메시지를 수신하면 트리거가 발생하여 에이전트가 실행됩니다. 이 에이전트는 메시지를 TIL(Today I Learned) 형식으로 변환한 후 GitHub에 코드를 푸시합니다. 푸시가 완료되면, `README.md` 파일에 해당 인덱스가 추가되고 마지막으로 완료 메시지가 발신됩니다.

### Core
- **Discord Webhook 설정**: Discord에서 메시지를 수신하여 워크플로우가 작동할 수 있게 Webhook을 설정합니다.
- **n8n Node 구성**:
  ```json
  {
    "name": "Discord Trigger",
    "input": "웹훅 URL",
    "output": "메시지 콘텐츠"
  }
  ```
- **GitHub Integration**: GitHub REST API를 사용하여 변환된 TIL 코드를 특정 저장소에 푸시합니다.
  ```json
  {
    "action": "push",
    "repository": "사용자/저장소",
    "file_path": "TIL/새로운파일.md"
  }
  ```
- **README.md 업데이트**: 푸시 완료 후 `README.md`에 새로운 항목을 추가합니다.

### Insight
n8n을 처음 사용해봤는데, 두 가지 요소만 알고 있으면 어렵지 않다고 생각됩니다. 각 노드가 어떤 입력을 받고 어떤 출력을 내보내는지를 정확히 이해하면 워크플로우를 쉽게 설계할 수 있습니다. n8n을 통해 복잡한 자동화도 간단히 구현할 수 있는 점이 인상적이었습니다.

**출처:** [Integrate Webhook with Discord using n8n](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook/)