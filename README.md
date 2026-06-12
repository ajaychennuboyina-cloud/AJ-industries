
from collections import Counter
import re

feedback = [
    "The battery life is poor",
    "Battery drains quickly",
    "The product is expensive",
    "Battery performance needs improvement",
    "Price is too high",
    "Packaging could be better"
]

# Simple keyword extraction
words = []

for comment in feedback:
    tokens = re.findall(r'\b[a-z]+\b', comment.lower())
    words.extend(tokens)

# Remove common words
stop_words = {
    "the", "is", "too", "be", "could", "and",
    "a", "an", "of", "to", "needs"
}

keywords = [word for word in words if word not in stop_words]

# Count frequency
common_issues = Counter(keywords)

print("Top product improvement areas:")
for word, count in common_issues.most_common(10):
    print(f"{word}: {count}")
