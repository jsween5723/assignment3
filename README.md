주제: 도서 관리 시스템 구현하기

요구사항:

1. Book 클래스 작성
    - Book 클래스는 제네릭 타입 T를 사용하여 책의 고유 식별자 타입을 나타냅니다.
    - Book 클래스는 다음과 같은 private 필드를 가집니다:
        - title (String): 책의 제목
        - author (String): 책의 저자
        - identifier (T): 책의 고유 식별자
    - Book 클래스의 생성자를 작성합니다:
        - public Book(String title, String author, T identifier)
        - 생성자 매개변수로 전달받은 값을 해당 필드에 초기화합니다.
    - Book 클래스에 다음과 같은 public getter 메소드를 작성합니다:
        - public String getTitle(): 책의 제목을 반환합니다.
        - public String getAuthor(): 책의 저자를 반환합니다.
        - public T getIdentifier(): 책의 고유 식별자를 반환합니다.
2. BookManager 인터페이스 작성
    - BookManager 인터페이스는 제네릭 타입 T를 사용합니다.
    - BookManager 인터페이스에는 다음과 같은 추상 메소드를 선언합니다:
        - void addBook(Book<T> book): 도서를 추가하는 메소드입니다.
        - void removeBook(Book<T> book): 도서를 삭제하는 메소드입니다.
        - List<Book<T>> searchByTitle(String title): 도서 제목으로 검색하는 메소드입니다.
            - 매개변수로 검색할 도서 제목을 전달받습니다.
            - 검색 결과를 Book<T> 객체들의 리스트로 반환합니다.
            - 검색 결과가 없으면 빈 리스트를 반환합니다.
        - List<Book<T>> searchByAuthor(String author): 도서 저자로 검색하는 메소드입니다.
            - 매개변수로 검색할 도서 저자를 전달받습니다.
            - 검색 결과를 Book<T> 객체들의 리스트로 반환합니다.
            - 검색 결과가 없으면 빈 리스트를 반환합니다.
3. BookShelf 클래스 작성
    - BookShelf 클래스는 BookManager 인터페이스를 구현합니다.
    - BookShelf 클래스는 내부적으로 ArrayList<Book<T>>를 사용하여 도서를 관리합니다.
    - BookShelf 클래스에는 다음과 같은 필드를 선언합니다:
        - private List<Book<T>> books: Book 객체들을 저장하는 ArrayList입니다.
    - BookShelf 클래스의 생성자를 작성합니다:
        - public BookShelf(): 기본 생성자로, books 필드를 빈 ArrayList로 초기화합니다.
    - BookShelf 클래스에서 BookManager 인터페이스의 메소드들을 구현합니다:
        - public void addBook(Book<T> book): 매개변수로 전달받은 도서를 books에 추가합니다.
        - public void removeBook(Book<T> book): 매개변수로 전달받은 도서를 books에서 삭제합니다.
            - 삭제할 도서가 존재하지 않으면 아무 작업도 수행하지 않습니다.
        - public List<Book<T>> searchByTitle(String title): 도서 제목으로 검색하는 메소드입니다.
            - 대소문자를 구분하지 않고 검색합니다.
            - 부분 일치하는 제목도 검색 결과에 포함시킵니다.
        - public List<Book<T>> searchByAuthor(String author): 도서 저자로 검색하는 메소드입니다.
            - 대소문자를 구분하지 않고 검색합니다.
            - 부분 일치하는 저자도 검색 결과에 포함시킵니다.
4. BookStack 클래스 작성
    - BookStack 클래스는 Stack<Book<T>>을 사용하여 도서를 관리합니다.
    - BookStack 클래스에는 다음과 같은 필드를 선언합니다:
        - private Stack<Book<T>> books: Book 객체들을 저장하는 Stack입니다.
    - BookStack 클래스의 생성자를 작성합니다:
        - public BookStack(): 기본 생성자로, books 필드를 빈 Stack으로 초기화합니다.
    - BookStack 클래스에는 다음과 같은 메소드를 작성합니다:
        - public void pushBook(Book<T> book): 매개변수로 전달받은 도서를 Stack의 맨 위에 추가합니다.
        - public Book<T> popBook(): Stack의 맨 위에 있는 도서를 제거하고 반환합니다.
            - Stack이 비어있는 경우, EmptyStackException을 throw합니다.
        - public Book<T> peekBook(): Stack의 맨 위에 있는 도서를 반환하지만 제거하지는 않습니다.
            - Stack이 비어있는 경우, EmptyStackException을 throw합니다.
        - public boolean isEmpty(): Stack이 비어있는지 여부를 반환합니다.
            - Stack이 비어있으면 true, 그렇지 않으면 false를 반환합니다.
5. Main 클래스에서 BookShelf와 BookStack 사용하기
    - Main 클래스에서는 다음과 같은 작업을 수행합니다:
        - String 타입의 식별자를 사용하는 BookShelf 객체를 생성합니다.
        - Integer 타입의 식별자를 사용하는 BookStack 객체를 생성합니다.
        - 사용자로부터 도서 정보를 입력받습니다. (제목, 저자, 식별자)
            - BookShelf의 경우 String 타입의 식별자를, BookStack의 경우 Integer 타입의 식별자를 입력받습니다.
        - 입력받은 도서 정보를 이용하여 Book 객체를 생성하고, BookShelf와 BookStack에 추가합니다.
        - BookShelf에서 도서 제목과 저자로 검색을 수행하고, 검색 결과를 출력합니다.
        - BookStack에서 도서를 꺼내고 (popBook), 꺼낸 도서의 정보를 출력합니다.
        - BookStack에서 맨 위의 도서를 확인하고 (peekBook), 해당 도서의 정보를 출력합니다.
        - BookStack이 비어있는지 확인하고 (isEmpty), 결과를 출력합니다.

위의 요구사항을 바탕으로 Book, BookManager, BookShelf, BookStack 클래스를 작성하고, Main 클래스에서 이를 활용하여 도서 관리 시스템을 구현해보세요.

과제 평가 기준:

- Book 클래스의 올바른 구현 (10점)
- BookManager 인터페이스의 올바른 선언 (10점)
- BookShelf 클래스의 올바른 구현 (20점)
- BookStack 클래스의 올바른 구현 (20점)
- Main 클래스에서의 BookShelf와 BookStack 활용 (20점)
- 코드의 가독성 및 주석 (10점)
- 컴파일 및 실행 결과의 정확성 (10점)