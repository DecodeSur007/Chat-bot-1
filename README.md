
*Functions:*

1. message_probability(user_message, recognised_words, single_response=False, required_words=[]):
   * This function calculates the probability that a user's message matches a response in the chatbot.
   * It takes four arguments:
      * user_message: A list of words representing the user's input.
      * recognised_words: A list of words that are considered keywords for a particular response.
      * single_response (optional): A boolean flag indicating if the response is a single word or phrase (True) or multiple sentences (False). Defaults to False.
      * required_words (optional): A list of words that must be present in the user's message for the response to be considered a match.
   * The function works by first initializing two variables:
      * message_certainty: This variable keeps track of how many words in the user's message match the keywords for the response.
      * has_required_words: This boolean flag is set to True initially and is turned to False if any of the required words are missing from the user's message.
   * It iterates through the user's message and checks if each word is present in the recognised_words list. If a match is found, message_certainty is incremented.
   * Then, it calculates the percentage of recognized words in the user message by dividing message_certainty by the total number of words in the recognised_words list.
   * The function checks if all the required words are present in the user's message using the has_required_words flag.
   * Finally, it returns the probability as an integer (0-100) based on the following conditions:
      * If all the required words are present (or it's a single response and no required words are specified), the probability is the calculated percentage multiplied by 100.
      * Otherwise, the probability is 0.

2. check_all_messages(message):
   * This function iterates through all the possible responses in the chatbot and determines the best match for the user's input.
   * It takes one argument:
      * message: A list of words representing the user's input.
   * It defines a nested function called response that simplifies the process of adding responses to the chatbot. This nested function takes four arguments:
      * bot_response: The actual response text the chatbot will give.
      * list_of_words: A list of words that the user's message needs to contain to trigger this response (keywords).
      * single_response (optional): Same as in the message_probability function.
      * required_words (optional): Same as in the message_probability function.
   * Inside the check_all_messages function, a dictionary called highest_prob_list is created to store the probability score for each potential response.
   * The function iterates through the code block defined after the response function definition. This block likely contains multiple calls to the response function, each defining a possible response the chatbot can give along with its keywords, single/multi-sentence flag, and any required words.
   * When calling the response function, it adds the response and its corresponding probability (calculated using the message_probability function) to the highest_prob_list dictionary.
   * After iterating through all the possible responses, the function finds the key in the highest_prob_list dictionary with the highest probability score. This key represents the best matching response for the user's input.
   * The function checks the probability score of the best match. If it's less than 1 (1% ), it returns a message indicating the chatbot didn't understand the user. Otherwise, it returns the best matching response text.

3. get_response(user_input):
   * This function preprocesses the user's input and calls the check_all_messages function to get the chatbot's response.
   * It takes one argument:
      * user_input: A string representing the user's text input.
   * The function uses regular expressions (re.split) to split the user's input into a list of words. This is likely done to make it easier to compare the user'
