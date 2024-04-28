# SME-Assignment

# Part2 : Setting up your Project

Took me only 15-17  min to setup the project. I have made the following changes: Copy pasted the inclde and lib in the smfl folder.

# Part2: Bug Fixing
Fixed the bug in the code. The bug was in following file: Took me only 20 min to fix the bug.

Space-Invaders/header/Gameplay/HighScore.h on line number 12, previously it was static class HighScore { public: static void saveHighScore(const HighScoreData& highScore); static HighScoreData loadHighScore(); };

changed it to

class HighScore { public: static void saveHighScore(const HighScoreData& highScore); static HighScoreData loadHighScore(); };

cause the static keyword was not needed during class declaration , it was overwrting the class objects.

Space-Invaders/header/Player/PlayerModel.h changed line 57 from static const int invincible_player_alpha = 170.f; to static const int invincible_player_alpha = 170;

cause the value was float and it was being assigned to int and it was required static.

Space-Invaders/source/Enemy/EnemyController.cpp , line 53 changed float x_offset_distance = (std::rand() % static_cast<int>(enemy_model->right_most_position.x - enemy_model->left_most_position.x)); to float x_offset_distance = static_cast<float>(std::rand() % static_cast<int>(enemy_model->right_most_position.x - enemy_model->left_most_position.x));	

cause the value was float and it was being assigned to int.

Space-Invaders/source/Gameplay/GameplayView.cpp , Space-Invaders/source/UI/MainMenu/MainMenuUIController.cpp

fixed the bug in the code by changing the following line: background_image->initialize(Config::background_texture_path, static_cast<float>(game_window->getSize().x), static_cast<float>(game_window->getSize().y), sf::Vector2f(0, 0));

Space-Invaders/header/Player/PlayerView.h, Space-Invaders/header/Player/PlayerController.h


You probably ran into a problem where PlayerController.h and PlayerView.h were including each other's headers directly, causing a circular dependency. To fix this, you opted for forward declarations in both files instead of directly including each other's headers. This means that instead of including the entire header file, you simply declare that the class exists, allowing the compiler to understand it without needing to see the full definition. This approach breaks the circular dependency and helps the compiler resolve dependencies more efficiently.


