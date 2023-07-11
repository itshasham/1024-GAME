#include<iostream>
#include<cstdlib>
#include<ctime>
using namespace std;

int down(int array[][4], int no_of_rows)
{
	int i, swap;
	int counter = 0;
	int counter1 = 0;
	for (int col = 0; col < 4; col++)
	{
		counter = 3;
		for (int row = 2; row >= 0; row--)
		{
			if (array[row][col] > 0)
			{
				i = row;
				array[i][col] = array[row][col];
				for (i = row; i < counter;)
				{
					if (array[i + 1][col] == 0)
					{
						swap = array[i + 1][col];
						array[i + 1][col] = array[i][col];
						array[i][col] = swap;
						counter1 = 1;
					}
					else if (array[i + 1][col] == array[i][col])
					{
						array[i + 1][col] = array[i][col] + array[i + 1][col];
						array[i][col] = 0;
						counter = i;
						counter1 = 1;
					}
					else
					{
						i++;
					}
				}
			}
		}
	}
	return counter1;
}
int up(int array[][4], int no_of_rows)
{
	int i, swap;
	int counter = 0;
	int counter1 = 0;
	for (int col = 0; col < 4; col++)
	{
		counter = 0;
		for (int row = 1; row < 4; row++)
		{
			if (array[row][col] > 0)
			{
				i = row;
				array[i][col] = array[row][col];
				for (; i > counter;)
				{
					if (array[i - 1][col] == 0)
					{
						swap = array[i - 1][col];
						array[i - 1][col] = array[i][col];
						array[i][col] = swap;
						counter1 = 1;
					}
					else if (array[i - 1][col] == array[i][col])
					{
						array[i - 1][col] = array[i][col] + array[i - 1][col];
						array[i][col] = 0;
						counter = i;
						counter1 = 1;
					}
					else
					{
						i--;
					}
				}
			}
		}
	}
	return counter1;
}
int right(int array[][4], int no_of_rows)
{
	int i, swap;
	int counter = 0;
	int counter1 = 0;
	for (int row = 0; row < 4; row++)
	{
		counter = 3;
		for (int col = 2; col >= 0; col--)
		{
			if (array[row][col] > 0)
			{
				i = col;
				array[row][i] = array[row][col];
				for (i = col; i < counter; )
				{
					if (array[row][i + 1] == 0)
					{
						swap = array[row][i + 1];
						array[row][i + 1] = array[row][i];
						array[row][i] = swap;
						counter1 = 1;
					}
					else if (array[row][i + 1] == array[row][i])
					{
						array[row][i + 1] = array[row][i] + array[row][i + 1];
						array[row][i] = 0;
						counter = i;
						counter1 = 1;
					}
					else
					{
						i++;

					}
				}
			}
		}
	}
	return counter1;
}
int left(int array[][4], int no_of_rows)
{
	int i, swap;
	int counter = 0;
	int counter1 = 0;
	for (int row = 0; row < 4; row++)
	{
		counter = 0;
		for (int col = 1; col < 4; col++)
		{
			if (array[row][col] > 0)
			{
				i = col;
				array[row][i] = array[row][col];
				for (; i > counter;)
				{
					if (array[row][i - 1] == 0)
					{
						swap = array[row][i - 1];
						array[row][i - 1] = array[row][i];
						array[row][i] = swap;
						counter1 = 1;
					}
					else if (array[row][i - 1] == array[row][i])
					{
						array[row][i - 1] = array[row][i] + array[row][i - 1];
						array[row][i] = 0;
						counter = i;
						counter1 = 1;
					}
					else
					{
						i--;
					}
				}
			}
		}
	}
	return counter1;
}
int main()
{
	bool counter = false;
	bool counter1 = false;
	bool counter2 = false;
	int row, col;
	int i, j;
	int number = 0;
	int number2;
	char press;
	int array[4][4] = {  };
	srand(time(0));
	while (!counter2)
	{
		i = rand() % 4;
		j = rand() % 4;
		number2 = (rand() % 2) + 1;
		if (array[i][j] == 0 && number2 != 3)
		{
			array[i][j] = number2;
			counter2 = true;
		}
	}
	counter2 = false;
	while (!counter2)
	{
		i = rand() % 4;
		j = rand() % 4;
		number2 = (rand() % 3) + 2;
		if (array[i][j] == 0 && number2 != 3)
		{
			array[i][j] = number2;
			counter2 = true;
		}
	}
	counter2 = false;
	for (row = 0; row < 4; row++)
	{
		for (col = 0; col < 4; col++)
		{
			if (array[row][col] > 0)
			{
				cout << array[row][col] << " | ";
			}
			else
			{
				cout << "  | ";
			}
		}
		cout << endl;
		cout << "----------------";
		cout << endl;
	}


	while (!counter)
	{
		number = 0;
		cout << endl << endl;
		cout << "For right press d" << endl;
		cout << "For left press a" << endl;
		cout << "For up press w" << endl;
		cout << "For Down press s" << endl;
		if (!counter) {
			cout << "Enter your desired move  ";
			cin >> press;
		}
		if (press == 'a')
		{
			number = left(array, 4);
		}
		else if (press == 'd')
		{
			number = right(array, 4);
		}
		else if (press == 'w')
		{
			number = up(array, 4);
		}
		else if (press == 's')
		{
			number = down(array, 4);
		}
		else
		{
			cout << endl << "Invalid input ";
			cout << endl;
		}

		for (row = 0; row < 4 && !counter1; row++)
		{
			for (col = 0; col < 4 && !counter1; col++)
			{
				if (array[row][col] == 0)
				{
					counter1 = true;
				}
			}
		}
		if (counter1 && number)
		{
			while (!counter2)
			{
				i = rand() % 4;
				j = rand() % 4;
				number2 = (rand() % 2) + 1;
				if (array[i][j] == 0 && number2 != 3)
				{
					array[i][j] = number2;
					counter2 = true;
				}
			}

		}
		for (row = 0; row < 4 && !counter; row++)
		{
			for (col = 0; col < 4 && !counter; col++)
			{
				if (array[row][col] == 1024)
				{
					cout << endl << "Congratulation!!!You Won. " << endl;
					counter = true;
				}
			}
		}
		for (row = 0; row < 4; row++)
		{
			for (col = 0; col < 4; col++)
			{
				if (array[row][col] > 0)
				{
					cout << array[row][col] << " | ";
				}
				else
				{
					cout << "  | ";
				}
			}
			cout << endl;
			cout << "--------------";
			cout << endl;
		}
		counter1 = false;
		for (row = 0; row < 4 && !counter1; row++)
		{
			for (col = 0; col < 4 && !counter1; col++)
			{
				if (array[row][col] == 0)
				{
					counter1 = true;
				}

			}
		}
		if (!counter1)
		{
			for (row = 0; row < 4 && !counter; row++)
			{
				for (col = 0; col < 4 && !counter; col++)
				{
					if (row == 0 && col == 0)
					{
						if (array[row][col] == array[row][col + 1] || array[row][col] == array[row + 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if ((row > 0 && row < 3) && (col == 0))
					{
						if (array[row][col] == array[row - 1][col] || array[row][col + 1] == array[row][col] || array[row][col] == array[row + 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if (row == 3 && col == 0)
					{
						if (array[row][col] == array[row][col + 1] || array[row][col] == array[row - 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if (row == 0 && (col > 0 && col < 3))
					{
						if (array[row][col] == array[row][col + 1] || array[row][col] == array[row][col - 1] || array[row][col] == array[row + 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if ((row > 0 && row < 3) && (col > 0 && col < 3))
					{
						if (array[row][col] == array[row][col + 1] || array[row][col] == array[row][col - 1] || array[row][col] == array[row - 1][col] || array[row][col] == array[row + 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if (row == 3 && (col > 0 && col < 3))
					{
						if (array[row][col] == array[row][col + 1] || array[row][col] == array[row][col - 1] || array[row][col] == array[row - 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if (row == 0 && col == 3)
					{
						if (array[row][col] == array[row][col - 1] || array[row][col] == array[row + 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if ((row > 0 && row < 3) && col == 3)
					{
						if (array[row][col] == array[row][col - 1] || array[row][col] == array[row + 1][col] || array[row][col] == array[row -
							1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
					else if (row == 3 && col == 3)
					{
						if (array[row][col] == array[row][col - 1] || array[row][col] == array[row - 1][col])
						{
							counter = false;
						}
						else
						{
							counter = true;
						}
					}
				}
			}
		}
		if (counter)
		{
			cout << "Game Over ! ";
		}
		counter2 = false;
		counter1 = false;
		cout << endl << endl;
	}
	system("pause");
	return 0;
} 
