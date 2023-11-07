# Word-Counter
 This program reads contents of a file and counts number of times each word appears in the file 
/**
 * This program reads contents of a file
 * and counts number of times each word appears in the file
 *
 * Samuel Yohannes
 * mi8854we@go.minnstate.edu
 * 04/09/2023
 *
 * Century College
 * CSCI 1081
 *
 * Professor Matthew Nyamagwa
 */
#include <iostream>
#include <string>
#include <fstream>
using namespace std;
//Structure named Words
struct Words{
	string name;
	int amount;
};

// Function Prototype
int amount(string a, string *b, int c);

int amount(string a, string *b, int c){
    int x = 0;
    for (int i = 0; i < c; i++){
        string lowercase_b = b[i];
        for (int w = 0; w < lowercase_b.length(); w++) {
            lowercase_b[w] = tolower(lowercase_b[w]);
        }
        if(lowercase_b == a){
            x++;
        }
    }
    return x;
}






int main(){
	// Defining Arrays
	const int SIZE = 50;
	Words words_arr[SIZE];
	string word[SIZE];
	string check[SIZE];
	//opens file
	ifstream file;
	file.open("words");
	string line;

	int i = 0;
	while (getline(file, line)){

		word[i]=line;
		i++;
	}
	//updates lenngth
	int length=i;
	file.close();
	i=0;
	for (string z:word){         //converting words to lowercase
		string lowercase_z = z;
	    for (int i = 0; i < lowercase_z.length(); i++) {
	        lowercase_z[i] = tolower(lowercase_z[i]);
	    }
	    //checks if word has been added
	    int len = i;
	    bool flag = false;
	    for (int j = 0; j<len;j++){
	    	if(check[j]==lowercase_z){
	    		flag = true;
	    		break;
	    	}
	    }
	    //adds words
	    if(!flag){
	    	check[i]=lowercase_z;
	    words_arr[i].name = lowercase_z;
	    words_arr[i].amount= amount(lowercase_z, word, length);
	    i++;
	    }
	}
	//Prints results
	for(int z=0; z<i; z++){
		cout<< words_arr[z].name << " "<< words_arr[z].amount << endl;
	}
	return 0;
}



option
eagle
popular
observation
formulate
cheat
cattle
peace
underline
simplicity
CHEAT
popular
observation
formulate
cattle
Peace
underline
formulate
cattle
PEACE
simplicity
cheat
popular
peace
underline
simplicity
