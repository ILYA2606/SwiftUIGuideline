# SwiftUIGuideline

Гайдлайн по разработке приложений на SwiftUI

## Оглавление

* [Именование](#Именование)
* [Ограничения](#Ограничения)
* [Property wrappers](#Property-wrappers)
* [Организация кода](#Организация-кода)
* [Ссылки](#Ссылки)

## Именование

- Любая View должна иметь суффикс `View` или компонента. Например: HomeView, FilterButton, TitleLabel, ValueSlider
- Замыкания у View должны иметь префикс `on`. Например: onTap, onSelection, onChange, onDrag
- View-модель должна иметь префикс названия View и суффикс `Model`. Например: HomeViewModel, FilterViewModel

## Ограничения

- Инициализация View и выполнение body должны быть максимально легкими. Не нагружайте их вычислениями
- Не используйте вертикальные паддинги в вертикальном стэке и горизонтальные паддинги в горизонтальном стэке. Вместо этого для отступов используйте `Spacer()` с фиксированной высотой/шириной
- Старайтесь не расширять View больше 100 строк. Если эту случается, то выносите компоненты в отдельные View
- Допускается выносить отдельные View в вычисляемые переменные или make-методы, если они должны принимать параметры
- Повторяющийся UI выносите в отдельную View, чтобы не допускать дублирования кода 

## Property wrappers

- @State - используется только внутри View
- @Binding - используется как внутри View, так и снаружи
- @StateObject - используется только внутри View. Жизненный цикл равен жизненному циклу View
- @ObservedObject - используется как внутри View, так и снаружи. Жизненный цикл управляется снаружи
- @EnvironmentObject - используется как внутри View, так и снаружи. Видимость объекта в рамках иерархии View
- @Environment - используется как внутри View, так и снаружи. Видимость во всем приложении
- @Published - используется как внутри ObservableObject, так и снаружи

## Организация кода

Соблюдайте следующую последовательность:
- public let
- public var
- internal let
- internal var
- private let
- private var
- public func
- internal func
- private func

Добавляйте пустую строку между разделами. Например:
```swift
let state: ViewState<[String]>
let title: String
    
@Binding var filterInfo: [String: Bool]

@State private var isFilterHidden = true
```

Последовательность врапперов:
- @Environment
- @EnvironmentObject
- @ObservedObject
- @StateObject
- @Binding
- @State
- var без враппера

## Ссылки

[Туториал от Apple](https://developer.apple.com/tutorials/swiftui/)  
[Первое знакомство с компонентами и переход из UIKit](https://github.com/SimpleBoilerplates/SwiftUI-Cheat-Sheet)  
[Все базовые вещи SwiftUI](https://fuckingswiftui.com)  
[Podlodka Crew #4](https://www.youtube.com/playlist?list=PLNSmyatBJig4yzwgVdhDJuSA4U8zhAqo7)  
[100 дней SwiftUI](https://www.hackingwithswift.com/100/swiftui)
