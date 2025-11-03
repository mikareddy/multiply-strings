class Solution(object):
    def multiply(self, num1, num2):
        if num1 == "0" or num2 == "0":
            return "0"

        # Initialize the result array
        result = [0] * (len(num1) + len(num2))

        # Reverse iterate over num1 and num2
        for i in range(len(num1) - 1, -1, -1):
            for j in range(len(num2) - 1, -1, -1):
                # Multiply the digits
                mul = (ord(num1[i]) - ord('0')) * (ord(num2[j]) - ord('0'))
                # Calculate positions in the result array
                p1, p2 = i + j, i + j + 1
                # Add to the current position
                sum_ = mul + result[p2]
                result[p2] = sum_ % 10
                result[p1] += sum_ // 10

        # Convert the result array to a string
        result_str = ''.join(map(str, result))
        # Remove leading zeros
        return result_str.lstrip('0')
