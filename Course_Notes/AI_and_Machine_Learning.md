# 59-2. AI AND MACHINE LEARNING:

WHAT IS AI?

- Artificial intelligence (AI) uses computers to simulate intelligence, allowing them to exhibit behaviors typically associated with humans, such as recognizing patterns, learning, making decisions, and solving problems.

Some examples:

- Virtual assistants: Siri, Alexa, Google Assistant
  
- Recommendation systems: Netflix, YouTube, Amazon product recommendations
  
- Self-driving cars and robotics: Tesla FSD, Waymo
  
- Chatbots: ChatGPT, virtual concierges
  
- Game play and analysis: Stockfish (Chess), AlphaGo (Go)


- AI is growing in importance, driven by increased computing power, availability of big data, and breakthroughs in AI research (i.e., the AI boom since ChatGPT’s release).

---

WHAT IS ML?
- Machine learning (ML) is a subset of AI that focuses on enabling computers to learn from data and improve without the need for explicit programming.

- Instead of hard-coded instructions (programmed by a human), ML algorithms identify patterns in data and make predictions or decisions based on those patterns.


IMAGEM


Some examples:
- Email spam filtering
- Personalized product recommendations
- Fraud detection (banking)
- Natural language processing (NLP)

  
-ML is the driving force behind many modern AI applications.

---
TYPES OF ML 

- Supervised learning
  - The model is trained on labeled data, where the correct answers are provided, to make predictions or classifications on new data.

- Unsupervised learning
  - The model is given unlabeled data and tasked with finding patterns, relationships, or groupings within the data.

- Reinforcement learning
  - The model learns by interacting with an environment, receiving rewards or penalties based on its actions to maximize its performance over time.

- Deep learning
  - A specialized subset of ML that uses multi-layered neural networks to handle large datasets and perform complex tasks like image recognition and natural language processing.

---

SUPERVISED LEARNING

Supervised learning trains the model on a labeled dataset.

- Each input provided to the model for training has a corresponding label.

- By examining these labeled examples, the model learns the relationship between the data and the given label.

- By training on labeled examples, the model learns to classify new, unseen data with high accuracy.


IMAGEM


Advantages:

- Highly accurate when labeled data is available.

Disadvantages:

- Requires large, labeled datasets, which can be expensive and time-consuming to create.

- output is limited to the labels in the training data

---

UNSUPERVISED LEARNING

Unsupervised learning trains the model on an unlabeled dataset.

- No predefined labels are provided.

- The model can discover patterns, structures, or relationships within the data (without human supervision).
  - It groups (clusters) similar data points based on shared features.


Advantages:

- No need for labeled data.

- Reveals hidden patterns.

Disadvantages:

- Interpretation and labeling of the results is required.

- Less accurate.

---


REINFORCEMENT LEARNING

- Reinforcement learning trains a model by rewarding or penalizing its actions in a given environment to maximize its performance over time.
  - The model learns to take actions that achieve the highest reward or best outcome.

- How it works:
  - The model (called an agent) interacts with an environment.
  - It takes an action and receives feedback (reward or penalty).
  - Over time, it learns which actions lead to the best results.


- Applications include:

  - Self-driving cars: Learning how to navigate safely by trial and error.
  - Game AI: Mastering strategies in games like Chess, Go, or video games.
  - Robotics: Teaching robots how to walk, pick up objects, or perform tasks.


Advantages:

- Capable of learning complex behaviors.

- Adapts to dynamic environments.

Disadvantages:

- Resource intensive.

- Risk of suboptimal learning if the reward system isn't properly designed.

---

DEEP LEARNING

Deep learning uses artificial neural networks to process and learn from large and complex datasets.

An artificial neural network is a computational model inspired by how biological neural networks like the human brain process information.

Data is passed through multiple layers of nodes (neurons), with each layer extracting increasingly abstract features.

The neural network can be trained using supervised, unsupervised, and/or reinforcement methods.

Structure:

Input layer

Hidden layers

Output layer

Advantages:

Deep learning excels at handling large, unstructured datasets like images, audio, and text.

Achieves state-of-the-art performance in tasks like image recognition, natural language processing (NLP), and more.

Disadvantages:

Resource intensive.

The model can be a "black box," making it difficult to interpret how it arrives at its decisions.



Supervised Learning

The model is trained on labeled data, where the correct answers are provided, to make predictions or classifications on new data.

Unsupervised Learning

The model is given unlabeled data and tasked with finding patterns, relationships, or groupings within the data.

Reinforcement Learning

The model learns by interacting with an environment, receiving rewards or penalties based on its actions to maximize its performance over time.

Deep Learning

A specialized subset of ML that uses multi-layered neural networks to handle large datasets and perform complex tasks like image recognition and natural language processing.

Artificial Intelligence

Machine Learning

Supervised Learning

Reinforcement Learning

Unsupervised Learning

Deep Learning




AI & Machine Learning | CCNA 200-301 (Day 59) | Generative AI
Predictive AI
Uses machine learning to analyze historical data and predict future outcomes or trends.

Examples: Security anomaly detection, weather forecasting.

Generative AI
Uses machine learning to learn patterns from existing data and create new content, such as text, images, or audio.

Examples: ChatGPT, Gemini, Midjourney, DALL-E, etc.

Artificial Intelligence
Machine Learning

Deep Learning

Predictive & Generative AI



Predictive AI

The model identifies patterns and correlations in past data.

Applications:

Healthcare: Predicting patient outcomes or disease progression.

Network security: Detecting anomalies that might indicate a potential threat or failure.

Traffic management: Predicting congestion based on historical and real-time traffic data.

Business forecasting: Predicting sales trends or customer behavior.

Weather Forecasting: Analyzing meteorological data to predict weather conditions.

Advantages:

Improves decision-making by providing actionable insights.

Detects potential problems before they occur (e.g., network issues or severe weather).

Disadvantages:

Requires high-quality, relevant historical data.

Accuracy depends on how well the patterns in past data generalize to new scenarios.





Generative AI

Generative AI learns patterns from existing data and creates new content such as text, images, and audio.

It focuses on producing outputs that resemble the input that it was trained on.

Examples:

cat

dog

cat

cat

dog

dog

cat

dog

Applications:

Text generation: ChatGPT, Gemini, Copilot

Image generation: Midjourney, DALL-E

Example: Generate an image of a cat.

Video generation: Sora (OpenAI), Veo (Google)

Advantages:

Great for creative tasks where human input is limited or time-consuming.

Disadvantages:

Risk of misuse (e.g., deepfakes, plagiarism).

Generated content is only as good as the quality of the training material.

Hallucinations.







AI & Machine Learning | CCNA 200-301 Day 59 (part 2) | Active AI in Networks
Predictive AI:
Traffic forecasting: Predict network traffic patterns to optimize bandwidth allocation and prevent congestion.

Security threat detection: Identify anomalies or suspicious patterns in real-time to mitigate potential security threats.

Predictive maintenance: Anticipate hardware failures by analyzing historical and current performance data, reducing downtime.

Generative AI:
Network documentation: Generate documentation about network configurations, policies, etc.

Configuration generation: Automatically generate configurations for network devices based on desired policies and requirements.

Network design: Suggest optimized network layouts or modifications tailored to specific business needs and workloads.

Troubleshooting: Produce solutions or diagnostics based on log files or error messages to resolve issues efficiently.

Script generation: Automatically generate network automation scripts (e.g., Python scripts to configure network devices).








AI & Machine Learning | CCNA 200-301 Day 59 (part 2) | Analyst Center
Cisco Catalyst Center (formerly DNA Center) features a variety of AI-enabled features to identify issues before they impact users, reduce the time required to resolve issues, and increase the performance and security of the network.

Features include...

AI Network Analytics

Uses AI to establish the baseline behavior of the network.

Provides insights and recommendations for optimizing network performance.

Continuously monitors the network to detect and predict anomalies.

Machine Reasoning Engine (MRE)

Uses AI to perform root-cause analysis when network issues arise.

Suggests resolutions or takes automated corrective actions without requiring manual intervention.

Reduces downtime by identifying and resolving issues faster than traditional methods.

AI Endpoint Analytics

Identifies and classifies devices on the network, providing detailed visibility.

Detects unauthorized devices or unusual behavior.

Simplifies device onboarding by automating profiling and segmentation.

AI-enhanced Radio Resource Management (RRM)

Optimizes wireless network performance by dynamically adjusting radio settings.

Uses AI to balance load, reduce interference, and improve coverage across wireless access points.



