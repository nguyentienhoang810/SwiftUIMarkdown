# SwiftUI memo

#### Table of Contents
1. [Navigation Bar](#NavigationBar)
2. [State](#State)
3. [Form and Section](#form-and-section)

## NavigationBar
```swift
struct ContentView: View {
    var body: some View {
        Form{
            Text("hi there")
        }
    }
}
```
![](imgs/nav/no-nav.png)

```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form{
                Text("hi there")
            }
        }
    }
}
```
![](imgs/nav/nav.png)

```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form{
                Text("hi there")
            }.navigationBarTitle("Nav-title")
        }
    }
}
```
![](imgs/nav/nav-with-title.png)

```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form{
                Text("hi there")
            }.navigationBarTitle("Nav-title", displayMode: .inline)
        }
    }
}
```
![](imgs/nav/nav-inline-title.png)

[Back to top](#Table-of-Contents)

## State
State make variable become mutable

### Immutable
```swift
struct ContentView: View {
    var body: some View {
        var name = ""
        Form {
            TextField("Enter your name", text: name)
            Text("Hello World")
        }
    }
}
```
![](imgs/state/no-state.png)

### Mutable - two way binding
```swift
struct ContentView: View {
    @State private var name = ""

    var body: some View {
        Form {
            TextField("Enter your name", text: $name)
            Text("Hello World \(name)")
        }
    }
}
```
![](imgs/state/state-binding.png)

[Back to top](#Table-of-Contents)

## Form and Section
Chỉ chấp nhận 10 rows trong 1 Form hoặc section
```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form {
                Section{
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                }
                Section{
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                    Text("Row")
                }
            }.navigationBarTitle("ForEach")
        }
    }
}
```
![](imgs/form-section/form-section.png)

Nếu muốn nhiều hơn 10 row trong 1 form thì sử dụng ForEach
```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form {
                ForEach(0 ..< 20) {
                    Text("Row \($0)")
                }
            }
            .navigationBarTitle("ForEach")
        }
    }
}
```
![](imgs/form-section/form-foreach.png)

[Back to top](#Table-of-Contents)
