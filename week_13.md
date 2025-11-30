프로그램 실습 1번

    #include <iostream>
    #include <vector>
    #include <algorithm>
    
    using namespace std;
    
    int main()
    {  
        vector <int> v1;
    
        for (int i = 0; i < 10; i++) {
            v1.push_back(10);
    		cout << "size: " << v1.size() << " ";
            cout << "capacity: " << v1.capacity() << endl;
        }
    }

프로그램 실습 2번

      int main()
      {
        vector<int> v1, v2, v3;
    
        v1.push_back(10);
        v1.push_back(20);
        v1.push_back(30);
        v1.push_back(40);
        v1.push_back(50);
    
        cout << "v1 = ";
        for (auto& v : v1) {
            cout << v << " ";
        }
        cout << endl;
    
        v2.assign(v1.begin(), v1.end());
        cout << "v2 = ";
        for (auto& v : v2) {
            cout << v << " ";
        }
        cout << endl;
    
        v3.assign(3, 6);
        cout << "v3 = ";
        for (auto& v : v3) {
            cout << v << " ";
        }
        cout << endl;
    
        v3.assign({ 5, 6, 7 });
        for (auto& v : v3) {
            cout << v << " ";
        }
        cout << endl;
    
        int& i = v1.at(0);
    
        cout << "v1 첫 번째 원소의 값:  " << i << endl;
    
        if (v1 == v2) cout << "v1과 v2는 같다." << endl;
        else cout << "v1과 v2는 다르다" << endl;
    
        i = 80;
        const int& j = v1.at(0);
    
        cout << "값을 변경 후 v1 첫 번째 원소의 값:  " << j << endl;
    
        if (v1 == v2) cout << "v1과 v2는 같다." << endl;
        else cout << "v1과 v2는 다르다" << endl;
      }

프로그램 실습 3번

        class Square {
        	int width;
        	int height;
        public:
        	Square(int x, int y) : width(x), height(y) {}
        
        	int area() { return width * height; }
        	void showWid() { cout << "가로 길이: " << width << endl; }
        	void showHei() { cout << "세로 길이: " << height << endl; }
        };
        
        int main()
        {
        	vector<Square> s;
        
        	for (int i = 0; i < 3; i++) {
        		s.push_back(Square(5 * i + 5, 10 * i + 5));
        	}
        
        	for (int i = 0; i < 3; i++) {
        		cout << "s" << i << "의 정보" << endl;
        		s.at(i).showWid();
        		s.at(i).showHei();
        		cout << "넓이: " << s.at(i).area() << endl;
        	}
        }

프로그램 실습 4, 5번

        int main()
        {
        	vector<int> v1(5);
        	v1.push_back(3);
        
        	cout << v1[5] << endl;
        	cout << v1.capacity() << endl;
        	cout << v1.size() << endl;
        }

프로그램 실습 6번

    int main()
    {
    	vector<int> v1(5);
    	v1.push_back(3);
    	v1.at(0) = 10;
    
    	cout << v1.capacity() << endl;
    	cout << v1.size() << endl;
    
    	for (int i = 0; i < v1.size(); i++) {
    		cout << v1.at(i) << " ";
    	}
    	cout << endl;
    }

프로그램 실습 7번

        void print_vec(const vector<int>& v, const string& label = "") {
        	if (label == "") {
        		for (int i = 0; i < v.size(); i++) {
        			cout << v[i] << " ";
        		}
        		cout << endl;
        	}
        	else {
        		cout << label << " ";
        		for (int i = 0; i < v.size(); i++) {
        			cout << v[i] << " ";
        		}
        		cout << endl;
        	}
        }
        
        int main()
        {
        	vector<int> v1(5);
        
        	for (int i = 0; i < v1.size(); i++) {
        		v1.at(i) = i + 1;
        	}
        
        	print_vec(v1, "v1의 값: ");
        
        	vector<int> v2(5);
        
        	for (int i = 0; i < v2.size(); i++) {
        		v2.at(i) = i + 6;
        	}
        
        	print_vec(v2, "v2의 값: ");
        
        	swap(v1, v2);
        
        	print_vec(v1, "swap 후 v1의 값: ");
        	print_vec(v2, "swap 후 v2의 값: ");
        
        	if (v1 < v2)
        		cout << "v1이 v2보다 작음" << endl;
        	else
        		cout << "v1이 v2보다 작지 않음" << endl;
        }

프로그램 실습 8번

        void backTest()
        {
            vector <int> v1;
        
            v1.push_back(10);
            v1.push_back(20);
            v1.push_back(30);
        
            int& it = v1.back();
        
            cout << "v1.back: " << it << endl;
            it = 60;
            cout << "v1[2]: " << v1[2] << endl;
            cout << endl;
        }
        
        void beginTest()
        {
            vector <int> v1;
            vector<int>::iterator it;
        
            v1.push_back(10);
            v1.push_back(20);
            v1.push_back(30);
        
            it = v1.begin();
        
            cout << "v1.begin: " << *it << endl;
            cout << endl;
        }
        
        void endTest()
        {
            vector <int> v1;
            vector<int>::iterator it;
        
            v1.push_back(10);
            v1.push_back(20);
            v1.push_back(30);
        
            it = v1.end();
        
            cout << "v1.end - 1: " << *(--it) << endl;
            cout << "v1.back: " << v1.back() << endl;
            cout << endl;
        }
        
        void clearTest()
        {
            vector <int> v1;
        
            v1.push_back(10);
            v1.push_back(20);
            v1.push_back(30);
        
            cout << "before clear. size: " << v1.size() << " capacity: " << v1.capacity() << endl;
            v1.clear();
            cout << "after clear. size: " << v1.size() << " capacity: " << v1.capacity() << endl;
            cout << endl;
        }
        
        int main(int argc, char const* argv[])
        {
            backTest();
            beginTest();
            endTest();
            clearTest();
            return 0;
        }

프로그램 문제 1번

        int main()
        {
        	vector<int> v;
        
        	int i, sum = 0;
        
        	while (true) {
        		cin >> i;
        		if (i == 0) break;
        		v.push_back(i);
        		sum += i;
        	}
        
        	print_vec(v);
        	cout << v.size() << endl;
        	cout << sum / v.size() << endl;
        
        	cout << count(v.begin(), v.end(), 5) << endl;
        }

프로그램 문제 2번

        int main()
        {
        	map<int, int> m;
        
        	int i;
        	int key;
        	int sum = 0;
        
        	while (true) {
        		cin >> i;
        		if (i == 0) break;
        		m[i]++;
        	}
        
        	map<int, int>::iterator it;
        	it = m.begin();
        
        	for (it; it != m.end(); it++) {
        		key = it->first;
        		sum += m.at(key);
        	}
        
        	cout << "sum: " << sum << endl;
        }
