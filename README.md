# CPP
프로그램 코드 1

탈 것이 부모 클래스인 코드와 개인적인 실습

    #include <iostream>
    #include <string>
    using namespace std;
    
    class Vehicle
    {
    private:
    	int person = 0; // private 멤버 변수 선언 및 초기화
    	int baggage = 0; // private 멤버 변수 선언 및 초기화
    public:
    	void ride() // 탑승
    	{
    		person++;
    	}
    	void load(int weight) { baggage += weight; } // 짐 싣기
    	void getOff() { person--; } // 하차
    
    	int getBaggage() { return baggage; } // baggage를 반환
    
    	int getPerson()  // 탑승인원 확인
    	{
    		return person; // person을 반환
    	}
    };
    
    class Cruise :public Vehicle // Vehicle 클래스를 부모로 하는 클래스 Cruise 정의
    {
    private:
    	int room; // private 멤버 변수 선언
    public:
    	void setRoom(int room) { this->room = room; } // this 키워드로 멤버 변수 room과 매개변수 room을 구분
    	void countPerson()
    	{
    		cout << "현재 Cruise 탑승 인원은: " << Vehicle::getPerson() << endl;     // 부모클래스 호출
    	}
    	void countBaggage() {
    		cout << "현재 Cruise 짐의인 실습

    #include <iostream>
    #include <string>
    using namespace std;

    // 부모 클래스 (기반 클래스)
    class Person {
    protected:
        string name; // protected 멤버 변수 선언
        int age; // protected 멤버 변수 선언
    
    public:
        Person(string n, int a) : name(n), age(a) {} // 매개 변수가 있는 생성자 정의
        // 문자열 n, 정수 a를 입력받아 각각 name, age를 초기화
    
    private:
        void introduce() { // name과 age를 출력하는 멤버 함수
            cout << "이름: " << name << ", 나이: " << age << endl;
        }
    
    public: // protected로 지정하여 자식 클래스에서 호출하는 방식으로도 사용 가능
        void callIntroduce() {
            introduce();
        }
    };
    
    // 자식 클래스 (파생 클래스)
    class Student : public Person { // Person 클래스를 public으로 상속받는 Student 클래스 정의
    private:
        string major; // private 멤버 변수 선언
    
    public:
        Student(string n, int a, string m) : Person(n, a), major(m) {} // 매개 변수가 있는 생성자 정의
        // 문자열 n, 정수 a, 문자열 m을 입력받아 각각 name, age, major를 초기화
        // name과 age는 부모의 생성자를 호출하여 초기화
    
        void study() { // name과 major를 출력하는 멤버 함수
            cout << name << " 학생이 " << major << " 전공 공부 중입니다." << endl;
        }
        /*void getIntroduce() {
            Person::introduce();
        }*/
    };
    
    int main() {
        Student s("홍길동", 21, "컴퓨터공학"); // Student 클래스의 객체 s를 생성
        s.callIntroduce();   // 부모 클래스 함수 사용
        s.study();       // 자식 클래스 함수 사용
        return 0;
    }

프로그램 코드 4

다중 상속 코드 실습

    #include <iostream>
    #include <string>
    using namespace std;
    
    class Teacher {
        int a = 10; // protected 멤버 변수 선언 및 초기화
        int b = 20;
    public:
        void teach() { // 문자열 출력 기능을 가진 public 멤버 함수
            cout << "강의를 하고 있습니다." << endl;
        }
        int sum() { return a + b; }
    };
    
    class Researcher {
        int a = 20; // protected 멤버 변수 선언 및 초기화
        int b = 40;
    public:
        void research() { // 문자열 출력 기능을 가진 public 멤버 함수
            cout << "연구를 하고 있습니다." << endl;
        }
        int sum() { return a + b; }
    };
    
    // 다중 상속
    class Professor : public Teacher, public Researcher { // Teacher, Researcher 클래스를 모두 상속받는 클래스 정의
    public:
        void introduce() { // 문자열 출력 기능을 가진 public 멤버 함수
            cout << "저는 교수입니다." << endl;
        }
    };
    
    int main() {
        Professor p; // Professor의 객체 생성
        p.introduce(); // 자식 클래스 멤버 함수 호출
        p.teach(); // 부모클래스 멤버 함수 호출
        p.research(); // 부모클래스 멤버 함수 호출
        cout << p.Teacher::sum() << endl; // a, b의 합을 출력
        cout << p.Researcher::sum() << endl; // a, b의 합을 출력
        return 0;
    }

프로그램 코드 5

    #include <iostream>
    #include <string>
    using namespace std;
    
    class Animal {
    public:
        void speak() { // 출력 기능을 가진 멤버 함수 정의
            cout << "동물이 소리를 냅니다." << endl;
        }
    };
    
    class Dog : public Animal { // Animal 클래스를 상속받는 클래스 Dog 정의
    public:
        void speak() { // 출력 기능을 가진 멤버 함수 정의
            cout << "멍멍!" << endl;
        }
    };
    
    class Cat : public Animal { // Animal 클래스를 상속받는 클래스 Cat 정의
    public:
        void speak() { // 출력 기능을 가진 멤버 함수 정의
            cout << "야옹!" << endl;
        }
    };
    
    int main() {
    
        Animal a1; // Animal의 객체 생성
        Dog a2; // Dog의 객체 생성
        Cat a3; // Cat의 객체 생성
    
        a1.speak(); // a1의 함수 호출
        a2.speak(); // a2의 함수 호출
        a3.speak(); // a3의 함수 호출
    
        Animal a = a2; // 객체 a2를 복사하여 Animal의 객체 a 생성
        Animal b = a3; // 객체 a3를 복사하여 Animal의 객체 b 생성
        a.speak(); // a의 함수 호출
        b.speak(); // b의 함수 호출
    
        return 0;
    }

과제 외 프로그램
다중 상속을 받는 클래스들을 직접 선언, 정의해보기

    #include <iostream>
    #include <string>
    using namespace std;
    
    class Animal {
    	string species; // 문자열 멤버 변수 선언
    	float weight; // 정수형 멤버 변수 선언
    public:
    	Animal(string s, float w) : species(s), weight(w) {} // 매개 변수가 있고 멤버 초기화를 하는 생성자 정의
    
    	void show() {
    		cout << "종: " << species << ", " << "무게: " << weight << "kg" << endl; // 멤버 변수를 출력하는 멤버 함수
    	}
    };
    
    class Fly {
    public:
    	void fly() { cout << "비행 가능" << endl; } // 출력 기능을 가진 멤버 함수
    };
    
    class Swim {
    public:
    	void swim() { cout << "수영 가능" << endl; } // 출력 기능을 가진 멤버 함수
    };
    
    class Bird : public Animal, public Fly { // Animal, Fly를 부모로 하는 Bird 클래스 정의
    public:
    	Bird(string s, float w) : Animal(s, w) {} // 매개 변수가 있고 멤버를 초기화 하는 생성자 정의
    
    	void speak() { cout << "짹짹" << endl; } // 출력 기능을 가진 멤버 함수
    };
    
    class Fish : public Animal, public Swim { // Animal, Swim를 부모로 하는 Fish 클래스 정의
    public:
    	Fish(string s, float w) : Animal(s, w) {} // 매개 변수가 있고 멤버를 초기화 하는 생성자 정의
    
    	void move() { cout << "파닥파닥" << endl; } // 출력 기능을 가진 멤버 함수
    };
    
    class Duck : public Animal, public Fly, public Swim { // Animal, Fly, Swim을 부모로 하는 Duck 클래스 정의
    public:
    	Duck(string s, float w) : Animal(s, w) {} // 매개 변수가 있고 멤버를 초기화 하는 생성자 정의
    
    	void speak() { cout << "꽥꽥" << endl; } // 출력 기능을 가진 멤버 함수
    };
    
    int main()
    {
    	Bird b("참새", 0.24f); // Bird의 객체 생성
    	Fish f("고등어", 1.6f); // Fish의 객체 생성
    	Duck d("집오리", 2.4f); // Duck의 객체 생성
    
    	b.show(); // 부모클래스 멤버 함수 호출
    	b.fly(); // 부모클래스 멤버 함수 호출
    	b.speak(); // 자식클래스 멤버 함수 호출
    
    	f.show(); // 부모클래스 멤버 함수 호출
    	f.swim(); // 부모클래스 멤버 함수 호출
    	f.move(); // 자식클래스 멤버 함수 호출
    
    	d.show(); // 부모클래스 멤버 함수 호출
    	d.fly(); // 부모클래스 멤버 함수 호출
    	d.speak(); // 자식클래스 멤버 함수 호출
    }
