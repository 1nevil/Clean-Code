# Clean code

- [1. What is Clean code](#chapter-1)
- [2. Meaningful name](#chapter-2)
- [3. Writing better function](#chapter-3)
- [4. Why code comment are bad](#chapter-4)

## <a id="chapter-1"></a> 1. What is Clean code

![Productivity and time relation in bad code](https://ptgmedia.pearsoncmg.com/images/chap1_9780132350884/elementLinks/1-4fig_martin.jpg)

#### When your code becomes messy and disorganized, your ability to work efficiently goes down over time.

#### Clean code are that clean , efficent ,readable ,testable

#### Clean code is that which each section can be easily understood at a glance

#### Clean code 5 parameters

1. Clear
2. Simple
3. Free of duplication
4. It leverages language constructs and expectations
5. Code should be consistent with existing codebase

#### Developers should make small improvements and cleanups to the code whenever they work on it, ensuring that the codebase remains clean and maintainable over time.

## <a id="chapter-2"></a> 2 - Meaningful name

### Variable name

Intention-revealing names - The intention-revealing names should **cleanly convey the intent** of the code author.

❌ **Avoid**

```
    public int calc(int x ,int y){
        int result;
        result = x * y;
        return result
    }
```

✅ **Instead of**

```
    public int calculate_product(int x ,int y){
        int product;
        product = x * y;
        return product
    }
```

#### Avoid missinformation

❌ **Avoid**

```
    List<Integer> userList = new ArrayList<>();
```

✅**Instead of**

```
    List<Integer> users = new ArrayList<>();
    List<Integer> bunchOfUser = new ArrayList<>();
    List<Integer> groupOfUser = new ArrayList<>();


```

#### Name should be pronounceable

❌ **Avoid**

```
   class AcntStmtRcd{
        private Date genddmmyy;
        private final String uid = 10;
   }
```

✅**Instead of**

```
    class AccountStatementRecord{
        private Date genrationTimeStamp;
        private final String userId = 10;
    }
```

### Class name

Use noun in nameing in class

❌ **Avoid**

```
    class ManageEmployees {
        // Class body...
    }

    class HandleRequests {
        // Class body...
    }

    class GenerateReports {
        // Class body...
    }
```

✅**Instead of**

```
    class EmployeeManager {
        // Class body...
    }

    class RequestHandler {
        // Class body...
    }

    class ReportGenerator {
        // Class body...
    }

```

### Method name

❌ **Avoid**

```
    // Incorrect: Unclear and abbreviated
    public int calc(int a, int b) {
        int r;
        r = a + b;
        return r;
    }

    // Incorrect: Too vague and lacks descriptive information
    public void process() {
        // Method body...
    }

```

✅ **Instead**

```
    // Correct: Descriptive and uses verbs to indicate action
    public int calculateSum(int num1, int num2) {
        int sum = num1 + num2;
        return sum;
    }

    // Correct: Clearly conveys the action the method performs
    public void generateReport(String reportType) {
        // Method body...
    }

```

### Use one term at a time

```
    fetchUser()
    getUser()
    retrieve()

    In above code meaning of the all name is same so "use one term" in intire application - be consistent
```

> your code should be read like sentences and peragraph

## <a id="chapter-3"></a> 3 Writing better function

#### function

Functions should be small, focused, and do one thing well. They should have a clear purpose and a descriptive name. Avoid long parameter lists, and ensure functions adhere to the Single Responsibility Principle.

❌ **Avoid**

```
    // Incorrect: Function with unclear purpose and long body
    public void processUserData() {
        // Long and convoluted code...
    }

```

✅ **Instead**

```
    // Correct: Function with clear name and single responsibility
    public void updateUserProfile(User user) {
        // Code to update user profile...
    }
```

#### Function Should Be Small

❌ **Avoid**

```

// Incorrect: Function with complex branching and steps
public void processPayment(Payment payment) {
    if (payment.isCreditCard()) {
        // Credit card processing...
    } else if (payment.isPayPal()) {
        // PayPal processing...
    }
    // More steps...
}

// Incorrect: Function doing too much work
public void processCustomerOrder(CustomerOrder order) {
    // Long and complicated process...
}

```

✅ **Instead**

```
    // Correct: Separate functions for payment methods
    public void processCreditCardPayment(CreditCardPayment payment) {
        // Credit card processing...
    }

    public void processPayPalPayment(PayPalPayment payment) {
        // PayPal processing...
    }


    // Correct: Break down into smaller functions
    public void validateOrder(CustomerOrder order) {
        // Validation logic...
    }

    public void calculateTotal(CustomerOrder order) {
        // Calculation logic...
    }
```

#### function size

function body size should be not greater than 7-8

❌ **Avoid**

```
    // Incorrect: Large function
    public void processInvoice(Invoice invoice) {
        // Many lines of code...
    }

    if you see name of the function it contains so much logic inside this function because of the naming convention

```

✅ **Instead**

```
    // Correct: Small and focused function
    public void calculateTotal(Invoice invoice) {
        // Calculation logic...
    }
```

### One Level of Abstraction

It is a concept in programming that suggests that a function should either deal with high-level logic or low-level details, but not both at the same time. This makes your code clearer and more organized.

**High-Level Details:** These are like the big picture concepts. Imagine explaining a process to someone without getting into the nitty-gritty details.

**Low-Level Details:** These are like the small, specific steps or actions that make up the process. It's like explaining the exact actions that need to be taken to accomplish a task.

❌ **Avoid**

```
    public void generateReport(Customer customer, List<Order> orders) {
    // High-level logic: Generating report headers, etc.

        for (Order order : orders) {
            // Low-level details: Generating order summary
        }
    }
```

✅ **Instead**

```
    public void generateCustomerReport(Customer customer) {
        // High-level logic: Generating report headers, etc.
        String customerReport = // ...

        for (Order order : customer.getOrders()) {
            customerReport += generateOrderSummary(order); // Using helper function
        }
    }

    private String generateOrderSummary(Order order) {
        // Low-level details: Generating order summary
        // Return the order summary...
    }

```

#### function name

❌ **Avoid**

```
    // Incorrect: Poorly named function
    public int c(int x, int y) {
        return x + y;
    }
```

✅ **Instead**

```
    // Correct: Meaningful function name
    public int add(int num1, int num2) {
        return num1 + num2;
    }
```

#### function argument

ideal number of argument should be 0

niladic function - 0 argument
monadic function - 1 argument

so it is more readable if number of argument should be less

❌ **Avoid**

```
    public class Calculator {

        public int calculateTotal(int num1, int num2, int num3, int num4) {
            return num1 + num2 + num3 + num4;
        }

        public static void main(String[] args) {
            Calculator calculator = new Calculator();
            int total = calculator.calculateTotal(10, 20, 30, 40);
            System.out.println("Total: " + total);
        }
    }

//this code should not be much readable

```

✅ **Instead**

```
    // Function should be small and focused
    public int calculateTotal(int... numbers) {
        // Function size: Small and focused
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        return total;
    }
```

#### DRY (Don't repeat your self)

❌ **Avoid**

```
    // Without DRY
    EX-1
    int area1 = length * width;
    int area2 = length * width;


    EX-2
    if (temperature > 30) {
        System.out.println("It's hot outside!");
    }

    if (temperature > 30) {
        System.out.println("Stay hydrated!");
    }
```

✅ **Instead**

```
    // With DRY

    EX-1
    int calculateArea(int length, int width) {
        return length * width;
    }

    EX-2
    int area1 = calculateArea(length, width);
    int area2 = calculateArea(length, width);

    void printMessage(String message) {
        System.out.println(message);
    }

    if (temperature > 30) {
        printMessage("It's hot outside!");
        printMessage("Stay hydrated!");
    }

```

## <a id="chapter-4"></a> 4. Why code comment are bad

### Types of valid comments.

#### 1 .Legel comment - Mainly for related to copyright of the code

```
    /*
        Copyright (C) 2017 The Android Open Source Project

        Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

         http://www.apache.org/licenses/LICENSE-2.0
        Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
    */
```

#### 2. Informative comment - As the name suggest Its give the informtion of the code.

```
    //format matched MM/DD/YY
    Pattern pattern = Pattern.compile("^(0[1-9]|[12][0-9]|3[01])[- /.](0[1-9]|1[012])[- /.](19|20)\d\d$")
```

#### 3. Explanation of Intent & Clarification - Write when the code is embiguous.

```
public class CommentExamples {

    public static void main(String[] args) {
        int x = 42;
        int y = 7;

        // Calculate the remainder of x divided by y
        int remainder = x % y;

        System.out.println("The remainder of " + x + " divided by " + y + " is " + remainder);

        ShoppingCart cart = new ShoppingCart();
        cart.addItem(19.99);
        cart.addItem(29.95);

        // Intent: Display the total amount in the shopping cart
        System.out.println("Total amount in the shopping cart: $" + cart.getTotalAmount());
    }
}

class ShoppingCart {
    private double totalAmount;

    // Intent: Add an item's price to the total amount
    public void addItem(double itemPrice) {
        totalAmount += itemPrice;
    }

    // Intent: Get the total amount in the shopping cart
    public double getTotalAmount() {
        return totalAmount;
    }
}

```

#### 4. Warning of Consequences - Explaining that a test takes a long time to run

```

//In java
@Test
public void testPerformance() {
    // Warning of Consequences: This test may take several minutes to complete due to extensive performance testing.
    // Consider running it selectively, not in every build.
    // Ensure your system is adequately resourced for accurate results.
    // If it consistently fails due to timeouts, investigate and optimize.
    // Disable in automated CI/CD pipelines if necessary.
    // Long-running tests can affect build times and resource usage.
    // Do not use this test for simple code changes; use it for performance profiling.

    // Test logic...
}

//In javascript

function fetchUserOrders(userId) {
    // Warning of Consequences: This function performs a slow database query.
    // It may cause a delay in response times.
    // Use it sparingly and consider optimizing the database query.

    // Database query logic...
}
```

#### 5.TODO Comment

```
// TODO: Implement error handling here
function processInput(input) {
    // your code...
}
```

#### 6.Documentation For Public APIs - Javadoc

```
/**
 * Calculates the area of the rectangle.
 *
 * @param length The length of the rectangle.
 * @param width The width of the rectangle.
 * @return The area of the rectangle.
 */
public double calculateArea(double l  ength, double width) {
    return length * width;
}

In this case, the Javadoc comment explains the purpose of the calculateArea method, its parameters (length and width), and its return value. It provides valuable information for developers who will use this method in their code.
```
