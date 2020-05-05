# SwiftUI memo

#### Table of Contents
1. [Navigation Bar](#NavigationBar)
2. [State](#State)
3. [Form and Section](#form-and-section)
4. [Picker](#picker)

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

### Picker
Normal picker
```swift
struct ContentView: View {
    @State private var numberOfPeople = 5
    
    var body: some View {
        Picker("Number of people", selection: $numberOfPeople) {
            ForEach(0 ..< 10) {
                Text("\($0) people")
            }
        }
    }
}
```
![](imgs/picker/normal-picker.png)

Đặt picker trong form → phải đặt form trong navigation view
```swift
struct ContentView: View {
    @State private var numberOfPeople = 5
    
    var body: some View {
        NavigationView {
            Form {
                Section {
                    Picker("Number of people", selection: $numberOfPeople) {
                        ForEach(2 ..< 100) {
                            Text("\($0) people")
                        }
                    }
                }
            }.navigationBarTitle("Picker")
        }
    }
}
```
![](imgs/picker/form-picker.png)

Segmented Picker Style & section header

```swift
struct ContentView: View {
    @State private var percentages = ["10%", "20%", "30%", "40%", "50%"]
    @State private var firstIndex = 2
    
    var body: some View {
        NavigationView {
            Form {
                Section(header: Text("choose one")) {
                    Picker("Segmented Picker Style", selection: $firstIndex) {
                        ForEach(0..<percentages.count) {
                            Text("\(self.percentages[$0])")
                        }
                    }.pickerStyle(SegmentedPickerStyle())
                }
            }.navigationBarTitle("Picker")
        }
    }
}
```

![](imgs/picker/SegmentedPickerStyle.png)

[Back to top](#Table-of-Contents)