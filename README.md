# SwiftUIGuideline

Гайдлайн по разработке приложений на SwiftUI

## Оглавление

* [Именование](#Именование)
* [Property Wrappers](#Property Wrappers)

## Именование

- Любая View должна иметь суффикс `View` или компонента. Например: HomeView, FilterButton
- Замыкания у View должны иметь префикс `on`. Например: onTap, onSelection, onChange, onDrag


## Property Wrappers

- @State - используется только внутри View
- @Binding - используется как внутри View, так и снаружи
- @StateObject - используется только внутри View. Жизненный цикл равен жизненному циклу View
- @ObservedObject - используется как внутри View, так и снаружи. Жизненный цикл управляется снаружи
- @EnvironmentObject - используется как внутри View, так и снаружи. Видимость объекта в рамках иерархии View
- @Environment - используется как внутри View, так и снаружи. Видимость во всем приложении
- @Published - используется как внутри ObservableObject, так и снаружи
