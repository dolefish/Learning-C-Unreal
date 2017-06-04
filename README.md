// Error codes on lines 38, 62 and 49 (see screen shot img for details).

#include "FBullCowGame.h"
#include <iostream>

int32 FBullCowGame::GetMaxTries() const { return MyMaxTries; }
int32 FBullCowGame::CurrentTry() const { return MyCurrentTry; }



FBullCowGame::FBullCowGame()
{
	Reset();
}

void FBullCowGame::Reset()
{
	// 
	constexpr int32 MAX_TRIES = 8;
	MyMaxTries = MAX_TRIES;

	const FString HIDDEN_WORD = "boobies";
	MyHiddenWord = HIDDEN_WORD;

	constexpr int32 CURRENT_TRY = 1;
	MyCurrentTry = CURRENT_TRY;

	return;
}


bool FBullCowGame::IsGameWon() const
{
	return false;
}

int32 FBullCowGame::GetHiddenWordLength() const
{

	return MyHiddenWord.length();
}

EWordStatus FBullCowGame::CheckGuessValidity(FString) const
{
	return EWordStatus::OK; //TODO Make actual error
}

int32 FBullCowGame::TimesPlayed()
{
	return TimesPlayed();
}


// recieves a valid guess, increments trun, and returns count
FBullCowCount FBullCowGame::SubmitGuess(FString Guess)
{
	//inctrement the turn number
	MyCurrentTry++;

	//setup a return variable
	FBullCowCount BullCowCount;

	// loop through all letters in the guess
	int32 HiddenWordLength = MyHiddenWord.length();
	for (int32 i = 0; i < HiddenWordLength; i++)
	{
		// compare letters against the hiddern word
		// NOTE: the i = HiddenWordCharacter and j = PlayerGuessCharacter
		for (int32 j = 0; j < HiddenWordLength; j++)
		{
			// if match than
			if (Guess[j] == MyHiddenWord[i]) 
				// if they're in the same place
				if (i == j)
			  // add bulls 
				{
					BullCowCount.Bulls++; // must be bulls
				}
			//else
				else 
				{
					BullCowCount.Cows++; // must be cows
				}
			  // increment cows
		}
	}
	return BullCowCount;
}
