#include <stdio.h>
int wordCount(char *str){
	int count=0;
	while (str[count]!='\0'){
		count++;
	}
	return count;
}

	char *arr[]={"splash","phantom","castle","pyramid","vampire","werewolf","zombie","dragon","demon","blood"};
int main (){
	int lives=5;
	int index;
	char *wordToGuess;
	int count;
	char guess;
	int flag=0;
	int ansCount=0;
	char displayArr[50];
	char guessedLetters[50];
    int guessedCount = 0;

	
	//player 1
	printf("choose number from 0-9 to guess: ");
    scanf("%d", &index);
	printf("\n");
	
	wordToGuess=arr[index];
	
	count=wordCount(wordToGuess);
	
	// display dashes (update when true )
	for (int i=0; i<count; i++){
		displayArr[i]='_';
	}
	displayArr[count]='\0';
	
		printf("Your word is %d letter long \n", count);
	
		for (int i=0; i<count; i++){
		printf ("_ ");
	}
		printf("\n");
	
	//player 2
	while (ansCount<count && lives>0){
		flag=0;
			printf("\n");
    		printf("\n\nGuess the word: ");
        	scanf(" %c", &guess);
    		printf("\n");
    		
    		//we will find if its repeated or not
        int alreadyGuessed = 0;
        for (int i=0; i<guessedCount; i++){
            if (guessedLetters[i] == guess){
                alreadyGuessed = 1;
                break;
            }
        }
        
        if (alreadyGuessed){
            printf("You've guessed that letter already!\n");
            continue; 
        }
        
       
        guessedLetters[guessedCount++] = guess;

    		for (int i=0;i<count;i++){
    			if (guess == wordToGuess[i] && displayArr[i]=='_'){
    				printf ("correct guess!\n\n");
    				displayArr[i]=guess;
    				flag=1;
    				ansCount++;
				}
			}
			
			if (flag == 0){
				lives--;
		    	printf("incorrect guess!\n\n");
			    printf("only %d lives left\n TRY AGAIN!", lives);
    		    printf ("\n");
			}
    		
    		for (int i=0; i<count; i++){
    			printf(" %c", displayArr[i]);
			}
	}
	 printf ("\n\n");
	
	if (ansCount == count){
		printf(" Congratulations! You guessed the word: %s\n", wordToGuess);
    } else {
        printf(" Game Over! The word was: %s\n", wordToGuess);
    }
    return 0;

	}
	
	
