# CPP
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
    		cout << "현재 Cruise 짐의 무게는: " << Vehicle::getBaggage() << endl; // 부모클래스 호출
    	}
    };
    
    class AirPlane :public Vehicle // Vehicle 클래스를 부모로 하는 클래스 AirPlane 정의
    {
    private:
    	int seat; // private 멤버 변수 선언
    public:
    	void setSeat(int seat) { this->seat = seat; } // this 키워드로 멤버 변수 seat와 매개변수 seat을 구분
    	void countPerson()    // 탑승인원 확인
    	{
    		cout << "현재 AirPlane 탑승 인원은: " << Vehicle::getPerson() << endl;     // 부모클래스 호출
    	}
    	void countBaggage() {
    		cout << "현재 AirPlane 짐의 무게는: " << Vehicle::getBaggage() << endl; // 부모클래스 호출
    	}
    };
    
    int main(int argc, char const* argv[])
    {
    	Cruise dolphin; // Cruise 클래스의 객체 생성
    	dolphin.ride();    // 부모클래스 멤버함수  접근
    	dolphin.load(10);  // 부모클래스 멤버함수  접근
    	dolphin.countPerson();     // 자식클래스 멤버함수 호출
    	dolphin.countBaggage(); // 자식클래스 멤버함수 호출
    
    	AirPlane cppAir; // AirPlane 클래스의 객체 생성
    	cppAir.ride();    // 부모클래스의 멤버함수 접근
    	cppAir.load(20);  // 부모클래스 멤버함수  접근 
    	cppAir.countPerson();     // 자식클래스 멤버함수 호출
    	cppAir.countBaggage(); // 자식클래스 멤버함수 호출
    
    	return 0;
    }
