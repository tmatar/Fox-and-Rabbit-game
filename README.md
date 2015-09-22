#include <iostream>
#include <iomanip>
#include <fstream>
#include <cstdlib>

using namespace std;

//structures
struct Fox
{
	int xIndex;
	int yIndex;
	int fedLevel;
	bool alive;
};

struct Rabbit
{
	int xIndex;
	int yIndex;
	int age;
	bool alive;
	
};


int main()
{
	//variable declaration and initalization
	char MyOutputFile[90] = { '\0' };
	ofstream outfile;
	int count = 0;
	int numRows = 0;
	int numCols = 0;
	int generations = 0;
	int seed = 0;
	double fracFox = 0;
	const double minFracFox = 0.05;
	const double maxFracFox = 0.95;
	const int minSeed = 0;
	const int minNumRows = 0;
	const int maxNumRows = 15;
	const int minNumCols = 0;
	const int maxNumCols = 15;
	const int minGenerations = 0;
	const int maxGenerations = 40;
	




	//For the output file
	for (count = 0; count <= 6; count++)
	{
		cout << "Enter the name of the output file: ";
		cin >> MyOutputFile;
		outfile.open(MyOutputFile);

		if (outfile.fail())
		{
			cerr << "ERROR: output file not opened correctly" << endl;
		}
		if (count == 6)
		{
			cerr << "ERROR: could not open output file after 6 tries" << endl;
			return 1;
		}
	}

	//For the numRows
	do
	{
		cout << "Enter the number of rows in the simulation grid: " << " ";
		if (!(cin >> numRows))
		{
			cerr << "ERROR: Cannot read number of rows" << endl;
			numRows = 0;
			cin.clear();
			cin.sync();
			count++;
		}
		if (numRows <= minNumRows || numRows >= maxNumRows)
		{
			cerr << "ERROR: Read an illegal number of rows for the board" << endl;
			count++;
		}
		if (count == 6)
		{
			cerr << "ERROR: could not read number of rows after 6 tries" << endl;
			return 2;
		}
	} while (numRows <= minNumRows || numRows >= maxNumRows);


	//For the columns
	do
	{
		cout << "Enter the number of columns in the simulation grid: " << " ";
		if (!(cin >> numCols))
		{
			cerr << "ERROR: Cannot read number of columns" << endl;
			numCols = 0;
			cin.clear();
			cin.sync();
			count++;
		}
		if (numCols <= minNumCols || numCols >= maxNumCols)
		{
			cerr << "ERROR: Read an illegal number of columns for the grid" << endl;
			count++;
		}
		if (count == 6)
		{
			cerr << "ERROR: could not read number of columns after 6 tries" << endl;
			return 3;
		}
	} while (numCols <= minNumCols || numCols >= maxNumCols);

	//Read number of generations
	do
	{
		cout << "Enter the number of generations: " << " ";
		if (!(cin >> generations))
		{
			cerr << "ERROR: Cannot read number of generations" << endl;
			numCols = 0;
			cin.clear();
			cin.sync();
			count++;
		}
		if (generations <= minGenerations || generations >= maxGenerations)
		{
			cerr << "ERROR: Read an illegal number of columns for the grid" << endl;
			count++;
		}
		if (count == 6)
		{
			cerr << "ERROR: could not read number of generations after 6 tries" << endl;
			return 4;
		}
	} while (generations <= minGenerations || generations >= maxGenerations);

	//for the seed
	do
	{
		cout << "Enter the seed for the random number generator: " << " ";
		if (!(cin >> seed))
		{
			cerr << "ERROR: Cannot read number of generations" << endl;
			seed = 0;
			cin.clear();
			cin.sync();
			count++;
		}
		if (seed <= minSeed || seed >= RAND_MAX)
		{
			cerr << "ERROR: Read an illegal seed" << endl;
			count++;
		}
		if (count == 6)
		{
			cerr << "ERROR: could not read the seed for the random number \n";
			cerr << "generator after 6 tries" << endl;
			return 4;
		}
	} while (seed <= minSeed || seed >= RAND_MAX);

	// for the fracFox
	do
	{
		cout << "Enter the initial fraction of squares in the grid containing foxes: " << " ";
		if (!(cin >> fracFox))
		{
			cerr << "ERROR: Cannot read the initial fraction of squares in \n the grid containing foxes" << endl;
			fracFox = 0;
			cin.clear();
			cin.sync();
			count++;
		}
		if (fracFox <= minFracFox || fracFox >= maxFracFox)
		{
			cerr << "ERROR: Read an illegal inital fraction of squares in \n the grid with foxes" << endl;
			count++;
		}
		if (count == 6)
		{
			cerr << "ERROR: could not read the initial fraction of squares \n";
			cerr << "in the grid containing no foxes after 6 tries" << endl;
			return 4;
		}
	} while (fracFox <= minFracFox || fracFox >= maxFracFox);





	return 0;
}
