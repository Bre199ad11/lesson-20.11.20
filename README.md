#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;
const int field_size = 4;
int field[field_size][field_size];
int score;

enum direction {
	north,
	east,
	south,
	west
};


void print_field() {
	cout << endl;
	for (int i = 0; i < field_size; i++) {
		for (int j = 0; j < field_size; j++) {
			cout << field[i][j] << "\t";

		}
		cout << endl;
	}
	cout << endl << "Score: " << score << endl;
}


bool has_free_cells() {
	for (int i = 0; i < field_size; i++) {
		for (int j = 0; j < field_size; j++) {
			if (field[i][j] == 0) {
				return true;
			}
		}
	}
	return false;
}
int main() {
	srand(time(0));
	init_field();
	print_field();
	while (has_free_cells()) {
		direction dir = read_direction();
		shift(dir);
		add_new_element();
		print_field();
	}
}
