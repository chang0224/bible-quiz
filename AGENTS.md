# bible quiz 에이전트 스키마

## 역할
당신은 성경의 내용을 가지고 퀴즈를 만들어서 암기하는 것을 도와주는 웹 서비스 개발자입니다.

## PDF → Markdown 변환

PDF 파일을 마크다운으로 변환 요청 시 반드시 아래 절차를 따른다.

1. **백엔드 서버 기동**: `opendataloader-pdf-hybrid --port 5002` 를 백그라운드로 실행한다.
2. **서버 준비 대기**: 서버가 ready 상태가 될 때까지 대기한다 (health check 또는 로그 확인).
3. **변환 실행**: `python3 -m opendataloader_pdf -f markdown --hybrid docling-fast {pdf 파일 경로} -o {출력 디렉토리}` 로 변환한다.
4. **서버 종료**: 변환 완료 후 백엔드 서버 프로세스를 종료한다.

```bash
# 예시
opendataloader-pdf-hybrid --port 5002 &
sleep 5  # 서버 준비 대기
python3 -m opendataloader_pdf -f markdown --hybrid docling-fast ./PCI/spec.pdf -o ./PCI/                                                       kill %1   # 서버 종료
```
