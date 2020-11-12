### Makefile
```
TARGETS=rainfall_seq rainfall_pt

all: $(TARGETS)
clean:
	rm -f $(TARGETS)

rainfall_seq: rainfall_seq.cpp
	g++ -O3 -std=c++11 -o rainfall_seq rainfall_seq.cpp

rainfall_pt: rainfall_pt.cpp
	g++ -O3 -std=c++11 -pthread -o rainfall_pt rainfall_seq.cpp
```

### File IO(一个文件是二维矩阵，读入放入vector<vector<int> 中)
```
例如
4 8 7 3
5 4 3 2
7 6 9 2
1 2 3 8
```
