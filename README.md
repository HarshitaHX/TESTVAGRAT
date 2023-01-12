 class Newspaper:
    def __init__(self, name, daily_price):
        self.name = name
        self.daily_price = daily_price
        
    def weekly_subscription_cost(self):
        return self.daily_price * 7

times_of_india = Newspaper("Times of India", 3)
hindustan_times = Newspaper("Hindustan Times", 2.5)
[12/01, 12:38 pm] SAHASGUDITECH: newspaper_list = [times_of_india, hindustan_times]
newspaper_dict = {'Times of India': times_of_india, 'Hindustan Times': hindustan_times}
[12/01, 12:38 pm] SAHASGUDITECH: from typing import List

def generate_combinations(newspapers: List[Newspaper], budget: float, combination: List[Newspaper]):
    if budget == 0:
        # Print the combination of newspapers and their cost
        print([(newspaper.name, newspaper.daily_price*7) for newspaper in combination])
        return
    if not newspapers:
        return
    if newspapers[0].daily_price*7 <= budget:
        # Include the first newspaper in the combination
        combination.append(newspapers[0])
        generate_combinations(newspapers[1:], budget - newspapers[0].daily_price*7, combination)
        combination.pop()
    generate_combinations(newspapers[1:], budget, combination)

# Create instances of the Newspaper class
times_of_india = Newspaper("Times of India", 3)
hindustan_times = Newspaper("Hindustan Times", 2.5)

# Define the budget
budget = 20

# Generate all possible combinations of newspaper subscriptions within the budget
generate_combinations([times_of_india, hindustan_times], budget, [])
