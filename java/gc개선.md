## 가비지 컬렉션에 의한 시스템 중단 시간을 줄이는 방법

- 옵션을 변경하여 GC의 성능을 높이기
    - young 영역과 old 영역의 힙 크기를 높여 GC의 빈도를 줄이는 것
    - 객체의 할당과 promotion을 줄이는 것

- 설정을 변경하여 GC의 성능을 높이기
    - 애플리케이션을 중단시킨 후에 GC를 병렬로 동시에 진행시키는 것
    - 애플리케이션과 GC작업을 동시에(concurrent) 진행시키는 것

- 개발자의 코드를 변경하여 GC의 성능을 높이기
    - Collection 등을 활용할 때 사용할 객체의 크기를 명시해주기
    - 스트림을 바로 사용하기
        - 변경 전: byte[] fileData = readFileToByteArray(new File("myfile.txt"));
        - 변경 후: FileInputStream fis = new FileInputStream(fileName);
    - 불변(Immutable) 객체 사용하기 → 스캔 범위를 줄임
