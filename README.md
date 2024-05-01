# chatbot-for-customer-service
#include <iostream>
#include <string>
#include <map>

using namespace std;

// Function to preprocess user input (e.g., convert to lowercase, remove punctuation)
string preprocessInput(string input) {
    // Implement your preprocessing steps here
    return input;
}

// Function to generate bot responses based on user input
string generateResponse(string input) {
    // Map of predefined responses based on user input
    map<string, string> responses = {
        {"hello", "Hello! How can I assist you today?"},
        {"help", "Sure, I'm here to help. What do you need assistance with?"},
        // Add more predefined responses here based on common customer inquiries
    };

    // Preprocess user input
    input = preprocessInput(input);

    // Search for a matching response
    for (const auto& pair : responses) {
        if (input.find(pair.first) != string::npos) {
            return pair.second;
        }
    }

    // Default response if no match found
    return "I'm sorry, I couldn't understand. Could you please rephrase?";
}

int main() {
    cout << "Customer Service Chatbot: Welcome! How can I assist you today?" << endl;
    cout << "You can start typing your questions or type 'exit' to quit." << endl;

    string userInput;
    while (true) {
        cout << "User: ";
        getline(cin, userInput);

        // Convert user input to lowercase
        transform(userInput.begin(), userInput.end(), userInput.begin(), ::tolower);

        // Check for exit command
        if (userInput == "exit") {
            cout << "Customer Service Chatbot: Goodbye! Have a great day." << endl;
            break;
        }

        // Generate bot response
        string response = generateResponse(userInput);
        cout << "Customer Service Chatbot: " << response << endl;
    }

    return 0;
}
