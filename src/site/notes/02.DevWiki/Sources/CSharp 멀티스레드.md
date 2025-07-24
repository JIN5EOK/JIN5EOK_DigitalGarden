---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/CSharp 멀티스레드/","noteIcon":"","created":"2025-05-23T01:22:37.522+09:00","updated":"2025-07-19T22:58:36.961+09:00"}
---

## 멀티스레드 구현 방법들

### Thread

- 가장 기본적인 방법, Thread를 직접 생성하고 관리할 수 있다
- ThreadPool에 의존하지 않으므로 실행시간이 오래 걸리는(장기간 ThreadPool에 반환되지 않는) 명령들은 Thread로 실행하는것이 적합함

### ThreadPool

- Thread 관리를 시스템이 관리하는 스레드를 위한 오브젝트 풀인 ThreadPool에 위임하는 방식

### Task

> 대부분의 작업은 Task만으로 가능

- 기본적으로 ThreadPool 기반으로 동작
- 다만 ThreadPool을 관리할 필요 없고 좀 더 추가적인 기능 사용 가능
    - 예를들어 async,await 패턴 사용 가능
- 가장 일반적인 사용 방식이고 실제로 대부분의 작업을 Task로 수행 가능

### Parallel

- 기본적으로 ThreadPool 기반으로 동작
- 데이터 병렬처리를 위한 방식, 여러가지 작업을 병렬로 수행할 수 있다

## 동시접근 제한

[멀티스레딩 환경에서의 동기화 문제](https://www.notion.so/1e6858a4236480adb9aeefe3f4b30946?pvs=21)

### lock

```csharp
private object _lock = new object();

lock (_lock)
{
// 임계 영역
}
```

- Monitor를 기반으로 동작
- 빠르고 쉽고 가볍다

### Monitor

```csharp
private object _lock = new object();

Monitor.Enter(_lock);
try
{
    // 임계 영역
}
finally
{
    Monitor.Exit(_lock);
}
```

```csharp
Monitor.TryEnter(_lock, 1000) // 1초 대기 후 실패
Monitor.Wait(_lock) // 현재 락 해제하고 대기
Monitor.Pulse(_lock) // 대기 중인 스레드 하나 깨우기
Monitor.PulseAll(_lock) // 모두 깨우기
```

- lock보다 더 세세한 컨트롤 원할 때 사용, lock과 달리 제어,조건 변수 사용가능

### Mutex

```csharp
private static Mutex _mutex = new Mutex();

_mutex.WaitOne();
try
{
    // 임계 영역
}
finally
{
    _mutex.ReleaseMutex();
}
```

### Semaphore / SemaphoreSlim

```csharp
SemaphoreSlim semaphore = new SemaphoreSlim(3); // 최대 3개 동시 허용

await semaphore.WaitAsync();
try
{
    // 임계 영역
}
finally
{
    semaphore.Release();
}
```

- **Semaphore**
    - 커널 객체 기반
    - 느리고 무겁지만 여러 프로세스간 동기화 가능
- **SemaphoreSlim**
    - Semaphore의 경량화 버전
    - 빠르고 가볍지만 같은 프로세스 내부에서만 동기화 가능

### Concurrent 계열 자료형 사용

- 멀티 스레드에서 안전한 컬렉션 자료형
- 일반 자료형보다 다소 무거움에 주의하자
- [https://learn.microsoft.com/ko-kr/dotnet/api/system.collections.concurrent?view=net-9.0](https://learn.microsoft.com/ko-kr/dotnet/api/system.collections.concurrent?view=net-9.0)

### Lazy 객체 사용

- 지연 초기화
- 객체 생성에 대해 스레드 안정성 제공

### interlocked 함수
단일 변수에 대한 원자적 연산 수행

### Vloatile 변수
단일 변수에 대한 연산이나 참조를 수행할 때 CPU 캐시가 아닌 메모리에서 수행하도록 함

---

### 관련 문서
[[02.DevWiki/Sources/유니티에서의 메인스레드와 멀티스레딩\|유니티에서의 메인스레드와 멀티스레딩]]
[[02.DevWiki/Sources/멀티스레딩 환경에서의 동기화 문제\|멀티스레딩 환경에서의 동기화 문제]]