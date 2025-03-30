# Markov Chain Weather Model

This project implements a simple Markov Chain using the `pomegranate` library to model weather transitions between "sun" and "rain" states. The model is defined with initial probabilities and a transition matrix, then used to generate a sequence of weather states.

## Prerequisites
Ensure you have Python installed along with the `pomegranate` library. If not installed, you can install it using:
```bash
pip install pomegranate
```

## File Overview
- **model.py**: Defines and runs the Markov Chain model.

## Code Explanation

### 1. Define Starting Probabilities
```python
start = DiscreteDistribution({
    "sun": 0.5,
    "rain": 0.5
})
```
This sets up the initial probability distribution where both "sun" and "rain" have an equal probability of occurring first.

### 2. Define Transition Probabilities
```python
transitions = ConditionalProbabilityTable([
    ["sun", "sun", 0.8],
    ["sun", "rain", 0.2],
    ["rain", "sun", 0.3],
    ["rain", "rain", 0.7]
], [start])
```
This table defines the probability of transitioning from one weather state to another. For example, if it is "sunny" today, there is an 80% chance it will remain sunny tomorrow and a 20% chance it will rain.

### 3. Create the Markov Chain Model
```python
model = MarkovChain([start, transitions])
```
This initializes the Markov Chain using the defined probabilities.

### 4. Sample Weather States
```python
print(model.sample(50))
```
This generates a sequence of 50 weather states based on the Markov Chain model.

## Running the Code
To execute the script, run:
```bash
python model.py
```
This will output a sequence of 50 weather states.

## Example Output
```bash
['sun', 'sun', 'rain', 'rain', 'sun', 'sun', 'sun', 'rain', ...]
```
Each element in the list represents the weather state for a given time step.

## Applications
- Weather prediction modeling
- Stock market trend analysis
- Natural language processing (text generation)

## License
This project is open-source and can be modified or distributed freely.

