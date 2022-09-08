# [CSS Functional Notation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions)

## **Syntax**

```css
selector {
  property: functional-notation([argument], ...);
}
```

## Functions

### Math Functions

#### clamp()

- It takes 3 comma separated expressions as its parameters in order of _minimum value_, _preferred value_ & _maximum value_.
- resultant value is calculated as:-

```css
max(minimum value, min(preferred value, maximum value))
```

#### min()

#### max()

#### calc()
