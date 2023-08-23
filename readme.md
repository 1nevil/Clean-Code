# Clean code

## 1. What is Clean code

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

## 2 - Meaningful name

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
