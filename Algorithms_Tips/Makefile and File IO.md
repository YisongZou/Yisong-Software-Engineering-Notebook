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
	
#include <bits/stdc++.h>

using namespace std;

int main(int argc, char *argv[]) {
  if (argc != 5) {
    cout << "Syntax: ./rainfall_seq <M> <A> <N> <elevation_file>" << endl;
    cout << "M = # of simulation time steps during which a rain drop will fall "
            "on each landscape"
            "point. In other words, 1 rain drop falls on each point during the "
            "first M steps of the"
            "simulation."
         << endl;
    cout << "A = absorption rate (specified as a floating point number). The "
            "amount of raindrops"
            "that are absorbed into the ground at a point during a"
            "timestep."
         << endl;
    cout << "N = dimension of the landscape (NxN)" << endl;
    cout << "elevation_file = name of input file that specifies the elevation "
            "of each point."
         << endl;
    return EXIT_FAILURE;
  }

  // Initialization of variables
  int timeSteps = stoi(argv[1]);
  float absRate = stof(argv[2]);
  int N = stoi(argv[3]);
  string elevation_file = argv[4];
  float runtime;
  vector<vector<int>> elevation(N, vector<int>());
  vector<vector<int>> absorb(N, vector<int>(N, 0));

  // open the file to read.
  fstream in("./" + elevation_file);
  string line;
  int ele; // Store elevation for each input unit
  if (in)  // file exists
  {
    int row = 0;
    while (getline(in, line)) // line does not contain newline of each line
    {
      stringstream ss(line);
      while (ss >> ele) {
        elevation[row].push_back(ele);
      }
      ++row;
    }
  } else // No such file
  {
    cout << "No such elevation_file" << endl;
    return EXIT_FAILURE;
  }

  return 0;
}

```
