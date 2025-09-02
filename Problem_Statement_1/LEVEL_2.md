### Level 2 (BONUS): The Smart Cipher Breaker
**The Challenge:** You've intercepted an encoded message, but you don't know the shift value. Create an intelligent function that can automatically find the correct shift by analyzing letter frequencies.

**The Problem:** English letters appear with different frequencies (E is most common, Z is least common). Your decoder should:
- Try all possible shifts (1-25)
- Score each result based on how closely it matches English letter frequency patterns
- Automatically return the most likely correct decryption
- Develop your own algorithm to score sentences which resemble English

> [!TIP]
> **Think About:** 
> How can you determine if a decoded message "looks like" English? What makes one decryption more likely than another?
> Message = input('Enter the encrypted data:')
message = Message.lower()
points_table = {}

for shift in range(1,27):
	points = 0
	for word in message:
		for letter in word:
			a = ord(letter)
			if ((97 + shift -1)<a<123):
				b = a - shift
			elif(96<a<(97+ shift)):
				b = a + 26 - shift
			else:
				b = a
			if b == 101:
				points += 5
			elif b == 116:
				points += 4
			elif b == 97:
				points += 3
			elif b == 111:
				points +=2
			elif b == 105:
				points += 1
			else:
				points += 0
	points_table[shift] = points
highest_points = max(points_table, key = points_table.get)
shift = highest_points
real_words =''
for word in Message:
	for letter in word:
		a = ord(letter)
		if ((97 + shift -1)<a<123):
			b = a - shift
		elif(96<a<(97+ shift)):
			b = a + 26 - shift
		elif ((65 + shift -1)<a<90):
			b = a - shift
		elif(64<a<(65+ shift)):
			b = a + 26 - shift
		else:
			b = a
		real_words += chr(b)
print(points_table)
print(shift)
print('Decoded message : ',real_words)
