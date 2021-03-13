# SwiftUIGuideline

Гайдлайн по разработке приложений на SwiftUI

## Оглавление

* [Именование](#Именование)
* [Ограничения](#Ограничения)
* [Использование Property wrappers](#Использование-Property-wrappers)
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
- Модификаторы всегда пишите с новой строки.
Рекомендуется:
```swift
MyView()
    .frame(height: 20)
```
Не рекомендуется:
```swift
MyView().frame(height: 20)
```

## Использование Property wrappers

- `@State` - используется только внутри View, чтобы изменить значение. Всегда делайте приватным
- `@Binding` - объявляет, что значение передается снаружи, но может изменяться и внутри View
- `@StateObject` - наблюдает за изменениями объекта и отвечает за сохранность данных. Используется только внутри View. Жизненный цикл равен жизненному циклу View. Всегда делайте приватным
- `@ObservedObject` - наблюдает за изменениями объекта, но не отвечает за сохранность данных. Используется как внутри View, так и снаружи. Жизненный цикл управляется снаружи
- `@EnvironmentObject` - общий объект, расшаренный для чтения/записи для конкретной иерархии View
- `@Environment` - общий объект, расшаренный для использования во всем приложении
- `@Published` - позволяет создавать наблюдаемые объекты, которые автоматически сообщают, когда происходят изменения. SwiftUI автоматически отслеживает такие изменения и повторно вызывает у View обновление body, в котором используются наблюдаемые объекты. Используется как внутри ObservableObject, так и снаружи

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
[Описания Property Wrapper-ов в SwiftUI](https://disk.yandex.ru/i/5C8sPIZwXVOC7g)
