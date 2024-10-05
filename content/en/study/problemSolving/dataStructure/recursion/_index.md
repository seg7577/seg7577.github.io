---
title: 📜RECURSION 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- **Recursion** is a programming technique where a function calls itself. Recursion is particularly useful in situations where a problem can be broken down into smaller subproblems that can be solved repeatedly. It allows complex problems to be expressed in a simpler form. Recursion relies on two key elements: a **base condition** and a recursive call.

- **Structure of a Recursive Function**: A recursive function typically has the following structure:
    - **Base Condition**: The condition that stops the recursion. Without it, the function would call itself infinitely, causing the program to never terminate.
    - **Recursive Call**: The part where the function calls itself. Each recursive call reduces the problem size, aiming to eventually reach the base condition.

- **Concept**:
    ```cpp
    // Recursion Example
    void func1(int N)
    {
        if (N == 0) // Base condition
            return;
        func1(N--);
    }

    int func2(int N)
    {
        if (N == 0) return 0;
        return N + func2(N - 1);
    }

    int fibo(int n)
    {
        if (n <= 1) return 1;
        return fibo(n - 1) + fibo(n - 2);
        // This recursion has exponential time complexity
        // This is because it repeats the same calculations, which can be optimized with dynamic programming
    }

    int main()
    {
        int n;
        cin >> n;
        func1(n);
        func2(n);
        cout << n;
        return 0;
    }
    ```

- **Problem**:
    ```cpp
    // BOJ 1629 - Multiplication
    #include <iostream>
    #define ll long long

    using namespace std;

    ll Recur(ll A, ll B, ll C) {
        if (B == 1) return A % C; // Base condition

        ll remainder = Recur(A, B / 2, C);

        if (B % 2 == 0) return remainder * remainder % C; // Case for even B
        else { // Case for odd B
            // Avoid overflow by calculating mod early
            remainder = remainder * remainder % C;
            return remainder * A % C;
        }
    }

    int main(void) {
        ios::sync_with_stdio(false);
        cin.tie(NULL);

        ll A, B, C;
        cin >> A >> B >> C;

        cout << Recur(A, B, C);
    }
    ```

    ```cpp
    // BOJ 1074 - Z
    #include <iostream>
    #include <algorithm>

    using namespace std;

    int func(int n, int r, int c) {
        if (n == 0) return 0; // Base condition
        int half = 1 << (n - 1); // Use bit shift to calculate half
        if (r < half && c < half) return func(n - 1, r, c); // Top-left quadrant
        if (r < half && c >= half) return half * half + func(n - 1, r, c - half); // Top-right quadrant
        if (r >= half && c < half) return 2 * half * half + func(n - 1, r - half, c); // Bottom-left quadrant
        return 3 * half * half + func(n - 1, r - half, c - half); // Bottom-right quadrant
    }

    int main() {
        ios::sync_with_stdio(0);
        cin.tie(0);

        int n, r, c;
        cin >> n >> r >> c;
        cout << func(n, r, c);
    }
    ```

    ```cpp
    // BOJ 11729 - Tower of Hanoi
    #include <iostream> 
    using namespace std;

    void func1(int a, int b, int n) {
        if (n == 1) { // Base condition
            cout << a << ' ' << b << '\n';
            return;
        }
        func1(a, 6 - a - b, n - 1);
        cout << a << ' ' << b << '\n';
        func1(6 - a - b, b, n - 1);
    }

    int main() {
        int n;
        cin >> n;
        cout << (1 << n) - 1 << '\n'; // Number of moves
        func1(1, 3, n); // Recursive function call to solve the Tower of Hanoi problem
    }
    ```

    ```cpp
    // BOJ 17478 - What is a Recursive Function?
    #include <iostream>
    using namespace std;

    int i = 0;
    bool flag, flag2;
    void func1(int n) {
        if (n == 0) flag = true; // Reached the "base" text after n iterations
        if (!flag) {
            for (int j = 0; j < i; j++) cout << "____";
            cout << "\"What is a recursive function?\"\n";
            for (int j = 0; j < i; j++) cout << "____";
            cout << "\"Listen carefully. Long ago, atop a mountain, there was a sage who knew everything.\"\n";
            for (int j = 0; j < i; j++) cout << "____";
            cout << "People asked him many questions, and he answered wisely.\n";
            for (int j = 0; j < i; j++) cout << "____";
            cout << "Most of his answers were correct. But one day, a scholar visited him and asked a question.\"\n";
        } else {
            return;
        }
        i++; // Increase indentation for the next recursive call
        func1(--n);

        if (flag) {
            if (!flag2) {
                for (int j = 0; j < i; j++) cout << "____";
                cout << "\"What is a recursive function?\"\n";
                for (int j = 0; j < i; j++) cout << "____";
                cout << "\"A recursive function is a function that calls itself.\"\n";
                for (int j = 0; j < i; j++) cout << "____";
                cout << "And that is how the professor answered.\n";
                flag2 = true; // To avoid printing these lines multiple times
                i--;
            } else {
                for (int j = 0; j < i; j++) cout << "____";
                cout << "And that is how the professor answered.\n";
                i--;
            }
        }
    }

    int main() {
        int n;
        cin >> n;
        cout << "Once upon a time, a computer science student asked a famous professor...\n";
        func1(n);
        cout << "And that is how the professor answered.";
        return 0;
    }
    ```

    ```cpp
    // BOJ 11729 - Tower of Hanoi (Alternate Implementation)
    #include <iostream>
    using namespace std;

    void func1(int a, int b, int n) {
        if (n == 1) { // Base condition
            cout << a << ' ' << b << '\n';
            return;
        }
        func1(a, 6 - a - b, n - 1);
        cout << a << ' ' << b << '\n';
        func1(6 - a - b, b, n - 1);
    }

    int main() {
        int n;
        cin >> n;
        cout << (1 << n) - 1 << '\n'; // Calculate total number of moves
        func1(1, 3, n); // Solve the problem
    }
    ```

