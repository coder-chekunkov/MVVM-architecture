### 🛠️📱Приложение для прототипирования. Архитектура MVVM.

Данный проект используется для быстрого прототипированя простых приложений с архитектурой MVVM. 
  
---

  <p align="center">
   <b> 📖 Теоретическая часть </b>  
 </p>
 
 `MVVM` (*Model-View-ViewModel*) - архитектурный паттерн проектирования. MVVM используется для разработки пользовательского интерфейса и разделяет ответственность за бизнес-логику и логику отображения. MVVM состоит из следующих частей:
  - `Model` - предоставляет собой данные, которые необходимо отобразить пользователю. В большинстве Android-приложений моделью выступает слой, отвечающий за получение данных с бэкэнда или базы данных. </br>
  - `View` - отвечает за отображение данных. В Android-приложениях View - это, зачастую, Activity или Fragment. </br>
  - `ViewModel` - отвечает за соединение Model и View. ViewModel подписана на обновления Model, а View подписана на ViewModel. При этом ViewModel не имеет явной ссылки на View. Часто подписки реализуются с помощью паттерна проектирования *Observer*.
  
`ViewModel` - класс, который отвечает за подготовку и управление данными для Activity или Fragment. Он также обрабатывает взаимодействие Activity / Fragment с остальной частью приложения (например, связь с классами бизнес-логики).

`LiveData` - класс, который хранит данные и реализует паттерн *Observer*. В отличие от обычных данных, LiveData учитывает жизненных цикл владельца, т.е. LiveData учитывает жизненный цикл компонента приложения, к которому была привязана (например Activity, Fragment, Service). </br>
LiveData предоставляет данные только наблюдателям, которые находятся в активном состоянии. Observer входит в активное состояние, когда соответствующий ему *lifecycle* переходит в состояние STARTED или RESUMED. Автоматически отписывает наблюдателей, когда их lifecycle переходит в состояние DESTROYED. 

---

  <p align="center">
   <b> ℹ️ MVVM-architecture - version 1.0 </b>  
 </p>
 
- **View** -> **ViewModel** -> **Model (Repository)**;
- Простая **стековая навигация** на базе фрагментов;
  - **Действия**: push/pop (запустить экран / выйти назад);
  - **Передача данных** между экранами в двух направлениях;
  - **Навигация** и передача данных полностью реализована на стороне ViewModel;
- **Поддержка SavedStateHandle**;
- Опциональная возможность **покрытия слоя ViewModel тестами**.
  
Приложение состоит из трёх экранов: главное меню, список с выбором пользователя и список с выбором языка программирования.
  - Экран главного меню хранит в себе данные о выбранном пользователе (фотография и имя), данные о выбранном языке программирования (иконка и название), а также кнопки для смены пользователя и языка программирования.
  - Экран выбора пользователя состоит из списка с набором пользователей, с каждым из которых можно произвести следующие действия: сделать выбранным, переместить вверх/вниз и удалить (в случае, если пользователь не выбран).
  - Экран выбора языка программирования состоит из списка с набором языков программирования, каждый из которых можно сделать выбранным.
  
На экранах выбора пользователя и языка программирования добавлена кнопка "Случайный элемент" в Toolbar, которая случайно выбирает элемент и меняет его статус на "выбрано". 
  
<p align="center">
 <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/mvvm_003.gif" width="220"/>
 <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/mvvm_001.jpg" width="220"/>
 <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/mvvm_002.jpg" width="220"/> <br/>
</p>

---

  <p align="center">
   <b> ℹ️ MVVM-architecture - version 2.0 </b>  
 </p>
 
 - **View** -> **ViewModel** -> **Model (Repository)**;
- Простая **навигация** на базе Jetpack Navigation Compose;
  - **Действия**: push/pop (запустить экран / выйти назад);
  - **Передача данных** между экранами в двух направлениях;
  - **Навигация** и передача данных полностью реализована на стороне ViewModel;
- **Поддержка SavedStateHandle**;
- Опциональная возможность **покрытия слоя ViewModel тестами**.
 
 <p align="center">
  <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/wiki_gif_version_2_001.gif" width="220"/>
  <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/wiki_image_version_2_001.jpg" width="220"/>
  <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/wiki_image_version_2_002.jpg" width="220"/> <br/>
  <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/wiki_image_version_2_003.jpg" width="220"/>
  <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/wiki_image_version_2_004.jpg" width="220"/>
  <img alt="GIF" src="https://github.com/coder-chekunkov/MVVM-architecture/blob/main/wiki_image/wiki_image_version_2_005.jpg" width="220"/>
</p>

---

📧 При возникновении каких-либо вопросов и предложений - свяжитесь со мной. <br/>
🤝 Спасибо, что заинтересовались работой.
