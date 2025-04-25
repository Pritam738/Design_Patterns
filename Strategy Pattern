# Understanding the Strategy Pattern: A Practical Guide

The Strategy Pattern is one of the classic behavioral design patterns, and it's all about **enabling flexibility in algorithm selection at runtime**. This article walks through what it is, when to use it, when not to, and its pros and cons — with practical questions answered.

---

## What is the Strategy Pattern?

The Strategy Pattern defines a **family of algorithms**, encapsulates each one, and makes them interchangeable. This allows the algorithm to vary independently from clients that use it.

> Simply put: Instead of hardcoding a behavior (like sorting), you inject a strategy (e.g., QuickSort or BubbleSort).

### Example:
```python
class SortStrategy(ABC):
    @abstractmethod
    def sort(self, data: list) -> list:
        pass

class BubbleSort(SortStrategy):
    def sort(self, data: list) -> list:
        # Bubble sort logic
        return sorted(data)  # Simplified

class QuickSort(SortStrategy):
    def sort(self, data: list) -> list:
        # Quick sort logic
        return sorted(data)  # Simplified

class DataSorter:
    def __init__(self, strategy: SortStrategy):
        self._strategy = strategy

    def set_strategy(self, strategy: SortStrategy):
        self._strategy = strategy

    def sort_data(self, data: list) -> list:
        return self._strategy.sort(data)
```

### Usage:
```python
sorter = DataSorter(BubbleSort())

if len(data) > 1000:
    sorter.set_strategy(QuickSort())

sorted_data = sorter.sort_data(data)
```

---

## Why Not Just Instantiate Strategy Directly?

You might ask:
> *Why do I need `DataSorter`? I could just use `QuickSort` or `BubbleSort` directly.*

Great question! Here's why:

- **Consistency & Abstraction**: The client code doesn’t care which algorithm is being used.
- **Encapsulation**: Strategy Pattern lets you change behavior without affecting the rest of the application.
- **Flexibility**: You can inject new algorithms with minimal code change.

---

## Why Use `set_strategy()` Instead of Reinitializing?

Another great question:
> *Why not just recreate the `DataSorter` with a new strategy?*

You *can* do that, but there are benefits to using `set_strategy()`:

| Reinitializing | Using `set_strategy()` |
|----------------|------------------------|
| Fine for small cases | Better for long-lived objects |
| Loses internal state | Preserves object state |
| Not dynamic | Easy to hot-swap dynamically |
| Less idiomatic | Object-oriented and clean |

If you're building a service that needs to switch strategies during its lifetime, `set_strategy()` is the way to go.

---

## When to Use Strategy Pattern

- When you have many variants of an algorithm
- When you want to switch behavior at runtime
- When behaviors should be interchangeable
- When code needs to follow **Open/Closed Principle**

## When *Not* to Use

- If you only have one fixed algorithm
- If the overhead of abstraction outweighs flexibility
- If behavior switching is never needed at runtime

---

## Advantages
- Promotes **open/closed principle**
- Improves code **readability and maintenance**
- Makes **unit testing and mocking easier**
- Allows **runtime flexibility**

## Disadvantages
- More classes to manage
- Slightly higher **complexity** upfront
- Can be **overkill** for simple use cases

---

## Final Thoughts

The Strategy Pattern is a powerful tool in your design toolbox. It lets you write code that is both **flexible and clean**, and allows for easy expansion in the future.

Use it when you foresee needing **multiple algorithms or behaviors** for a single task, and want the ability to swap them dynamically.

---

### Practice Prompt:
Implement a file compression tool that supports different compression algorithms (e.g., ZIP, TAR, GZIP) using the Strategy Pattern. Make sure the compression strategy can be swapped at runtime.

Happy coding!

