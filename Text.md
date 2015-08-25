# Сначала стайлгайд, или как перейти на компонентный подход
## 1. Обложка 

Привет! Этот доклад будет о разработке при помощи UI стайлгайда, или style-guide-driven development, очень популярном сейчас подходе.

Я буду делать больший акцент на автоматизации этого процесса, потому что некоторые его части можно поручить роботам и специальным инструментам.

## 2. Обо мне

Прежде чем мы начнем, расскажу о себе. Меня зовут Варя, я разработчик интерфейсов, сейчас живу в Хельсинки.

Я работаю в компании SC5 Online, мы консультируем другие компании в области фронтенда и делаем для них всякие сложные штуки. В частности, мы помогаем им внедрить у себя практику компонентного подхода к разработке веб-интерфейсов и стайлгайды.

Можно сказать, это моя основная специализация: разработка и поддержка долгоживущих проектов, библиотеки компонент, стайлгайды.

## 3. Улучшение процесса разработки

Если в двух словах описать, что делает наша компания или что я делаю для наших клиентов, то это будет "улучшение процесса разработки".

Конечно, я ещё пишу CSS и JavaScript. Но это всё второстепенные вещи, а главное дело — исправить недостатки их процесса, понять что в процессе плохо и изменить это. Часто бывает, что меняем мы это при помощи нами написанных вспомогательных инструментов.

Именно это случилось в случае стайлгайдов и разработки при помощи стайлгайдов. Нам показалось, что есть некоторые проблемы, и мы искали пути к их решению. Проблемы такие:

## 4. Метод старой школы

Здесь я нарисовала всем нам знакомый, канонический, путь разработки веб сайтов. Обычно происходит так:

- Дизайнер делает макет в фотошопе. Или несколько макетов, для каждой страницы.
- Затем макет отправляется к верстальщику или разработчику интерфейсов. На самом деле это может быть тот же самый дизайнер, но роли в проекте всё равно разные, то есть это следующая стадия процесса.
- Когда вёрстка готова, у нас есть шаблон с нужными стилями и яваскриптом. Мы можем интегрировать его в реальный продукт, всё это отправляется на сервер и затем это видно в продакшене.

Такой вот типичный процесс.

## 5. Потери на процессе

Теперь давайте приглядимся.

С учетом времени это должно выглядеть вот так. Сначала есть выделенное время для дизайна. Затем предусмотрено время для вёрстки с учётом того, что дизайн к тому времени уже готов. Ну и немного времени на интеграцию. Выглядит чики-пуки. Но проблема в том, что так как запланировано никогда не происходит.

В реальном мире дизайнеру требуется больше времени, чтобы нарисовать макет. Может быть изначально время было оценено неправильно. Но обычно проблема в том, что появляются новые требования уже тогда, когда они начали рисовать. В любом случае, дизайн приходит с опозданием.

Затем вёрстка. Мы не могли начать сразу, потому что за время ожидания уже переключились на другой проект. Начали позже. Но затем оказалось, что всё равно вёрстку нужно выбросить и начать сначала, потому что опять появились новые требования и дизайнер снова всё перерисовал.

До интеграции вообще никогда не доходит, потому что на слайде уже нет места.

И это только про одну итераццию. На самом деле интерфейс надо ещё и поддерживать и такие вещи случаются снова и снова. То есть картина на самом деле даже хуже. Каждый раз когда мы получаем новую картинку от дизайнера, надо понять, что было изменено и соответственно менять код. А может быть даже всё выкинуть.

Ну и про страницы то же самое. Макеты не говорят о том, какие части общие между страницами, это нужно вычислять самим в уме, и делать это надо много раз подряд.

## 6. Метод старой школы

Проблемы этого метода обычно такие:

Продукт получается визуально неконсистентным. То есть страницы немного разные, или не части интерфейса, которые должны быть согласованы, выглядят по разному. Требуются отдельные специальные усилия, чтобы всё приводить к единому стилю и предложенный процесс не предлагает никакого решения сделать это автоматически.

Код может быть неконсистнтным. Особенно на больних вебсайтах. Когда мы тут подправили, здесь подкрутили, часто бывает, что появляется копипаст или неиспользуемый код неудалён или вообще всё надо было делать по-другому. Опять же, вполне возможно держать всё в порядке, но на это требуются специальные усилия.

Если нужно в интерфейсе что-то изменить, это может быть сложным. Даже если говорить о каком-то небольшом изменении вроде "новый вид всех кнопок или всех контролов форм на сайте", задача не такая уж и тривиальная, просто потому что мест с этими контролами может быть очень много и везде написан разный css.

Всё это занимает много времени ведь с неконсистетностью мы боремся каждый раз.

И даже не имеет значения насколько успешно мы с нею боремся, потому что в следующей итерации это проблемы всплывут снова. Мы может быть и исправляем что-то в коде или интерфейсе, но недостатки процесса всегда сохраняются.

## 7. Веб сайт как система

С этими проблемами сталкиваются веб разработчики по всему миру, и од

So, the recent strong movement in the frontend development is to understand that we  are not coding the pages. We are developing websites, which are systems much more complex than just a set of pages.

Understaning this results into different way of developing.

## 8. Modular CSS Architecture

To do so people came up with modular solutions for CSS. It can be Object-Oriented CSS, SMACSS, BEM, atomic design. Does not really matter what to choose, they all serve the same purpose. With them we can modularize the interface and develop it as a set of components.

## 9. Modular CSS process

Such an approach may provide the process changes as well. So that every component can has its own development cycle.

Of course, there can be difficulties in developing each of them any way. But the modular process is much easier to manage. As they've said "divide and rule".

It is easier to estimate when talking about these small pieces. Easier to asign them to different team members and so share the work. It is easier to test the result, and the tests can even be automated. And if a problem appears, it is easier to solve becaue it is scoped.

## 10. Getting out of your comport zone

However all this modularizing thing is very easy to be said. But it is much harder to be done.

Mostly because it is out of our comfort zone. We see the pages, not sets of components. Moving towards the components-based interfaces is cultural challenge, it needs us to fix something in our mindset.

## 11. Living style guides

There is a solution to help us with it, the living style-guides.

Before the style guides was mostly used to document the work of visual designers. Often is was a PDF file with the used colors, basic interface elements and so one.

But this was not very helpful for the frontend developers to take in practise this component approach because it was also a drawing.

Much better thing are the living style-guides. They are web pages which fit all the used interface pieces. And these interface is rendered with exactly the same styles which are used in the product. So such a style guide reflect all the changes.

## 12. Style-guide-driven development

We can go even further. If there is such a living style guide, why not to develop style guide fist?

If a new interface piece appears, we first code it in the style guide. When it is finished and polished, we bring it into real system. The style guide website uses the same styles, so it is almost zero amount of work to bring ready-made component into the product.

This is like "documentation first", but for user interfaces.

The idea sounds very good. But again — the cultural challenge. But also a technological one.

## 13. The tool we missed

We can do nothing with the mindsets. It is a chanllenge for each of us to overcome on our own. But as engineers we can make it so that all the technical things would happen automatically.

This is what we though it our company. We were very excited about using this style-guide-driven and component approach. So we wanted to implement it in our projects. But we also wanted that most of the technical things about that were solved in advance. This is to make the process as smooth as possible.

There is a lot of living style guide solutions already but we missed some features. So we developed our tool which actually extends one existing solution.

We call it simply. Just style guide generator by SC5. Here you can see a link to its page. It is actually open source tool, so there is its github repository with all the commmits and issues. Check it out.

And I will show and explain its features and the development workflow we have.

## 14. Easy to start

We wanted the tool to be easy to start. So, it is an npm package. You can install it into your website. The run a command and the tool takes your CSS and automatically builds a style guide.

If works for the popular syntaxes such as pure CSS, SASS and LESS. We do not know in advance what is used in the next project. So, the tool should work everythere.

Our style guide generator extends another one, KSS. It uses KSS as a dependant package. So, the documentation for the components goes in style files in KSS syntax. In general the idea of keeping the documentation close to code is nice and promises benefits. And KSS as a syntax became quite popular so we wanted for most of the project to e able to try our tool right away.

It is gulp- and grunt- integrated out of box. This is very important for the style-guide-driven process to happend. Because no one would use additional command when developing. But if the style guilde website appears after you run your usual gulp command, this is completely different story.

So, let me show you in code.

This code belongs to a pattern library of one client of ours. They are a very big Finish, Sweden and Estonian company, a mobile operator Elisa. They have a lot of websites which share the same style. So, they have this repository of components.

`ls public_html/scss`

These are the style files.

If we open one of them, for example _molecules.scss, you can see that inside are comments which document the code. This is the KSS syntax. It says what is the component below, what markup it needs, what are its possible modifications.

Then in `package.json` of this project you can see that there is `sc5-styleguide` package installed. This means that I can run it.

In here the generator is used with Gulp, so I run its task (`gulp styleguide-watch`).

It does something and runs the local server. Let's see what it is.

So, this is the website. The components from css files are represented here. This is a list of them. We were looking for a subset of them called 'Molecules' Here they are (click).

So, every component is described. There is a list of possible modifiers. Then, all the modifications are rendered right here. And this is real HTML, it works.

Each example can be also opened in a full screen mode. So, pure page with one component only. This is very useful for automated UI testing. When a new version of the pattern library appears, a robot can visit all the links, take screenshots and compare previous version and current one. So if padding is wrong or a border is missing, it is easy to spot.

Then, below there is a markup needed for this component. This is what is used to render it above.

And there is also the corresponding piece of CSS. Just for your information.

## 15. Easy to keep up to date

So, as you could see, the style guide is automatically generated from the actual source code of the product website. It takes the information from the documented code.

And there is one more feature I need to show you. The Angualr directives support.

As you could see, it is needed to document the markup for every component so that the tool knew what to render. However this might be not very useful when mantaining. If markup changes, it makes a developr to fix it here first and then go and fix it in the product. We did not like it, so we added Angualr directive support.

For example here, (`public_html/scss/_angulardirectives.scss`) there are our angular components. And it is declared what is a directive to render it.

Then, if we go to its styleguide page, we can see that it is rendered normally. This is because the styleguide loads the directory and applies it. So, everything works exactly like in the product application.

When we will need another markup and so change the directive, it automatically changes in the styleguide. There is no need to reflect these markup changes manually.

## 16. Use as a development playground

Then, as our main goal is to encourage developers to focus on the style guide first, we needed to make this generated website a good development playground. So, the next features serve for that.

Let us open the molecules again. Now I will change their styles. Let us change this color for example.

After saving the document you can see that the website refreshes itself and new styles are applied.

(scroll)

Then, we have this nice "Designer tool" button here. It opens a panel where the variables and their values are listed. It shows only the variables used in the current component. If I scroll down, it changes the list.

It is always possible to show them all. But for large systems it is usually such a long list. So, this related variables feature is a pretty nice feature.

This is possible because in the tools we are using a real parser. So, no regexps. And this helped us to implement next features.

Then, the values here are edittable. Let's try. I will change this blue color into green. As you see, it changes the appearence. And if I go and check in the file system, you cal see that it made changes there.
This is very helpful for non-technical guys to fix something. Especially at the final stage, when interface is being polished. And the changes are in real styles. Later they can be commited into the repository.

Again, this is only possible with using real parser. We use Gonzales. The regexp solutions we tried eairlier, are not that good. So, we also came to this wisdom of no-regexp.

Then, another good thing is that I can find all the components where this variable is used. This is a list of them. So, when changing something, I can visually check everything affected.

Also it is possible to search through the CSS code of components. For example, all the components using background. Or all the components, whose markup includes our inputs. If we had changed the input, we could check it everythere.

## 17. Cross-company style guide process

So, we use this generator and it is very much embedded into our process. For example, this pattern library belongs to our client. And their websites use it to get coherent interfaces.

However, this is never ending process and we obviously need different teams not only use the library but also to contribute into it. This is where our tools helps. When the developers need to fix a component, they do not do it in there products. They generate the styleguide over the library website and develop there. Then. they contribute into the library with pull requests. The same goes for new components.

The library in versioned and is also a package, but this is a different story.

Our client says that it saves them 25% or working time.

## 18. Style Guide Generator by SC5

We are trying it out right now and I can say that this is a veru benefitable approach.

We have our UI documented and well structured. The system encourages us to keep it clean.

Developing the component isolated, we can quickly test them. Also these searching features help a lot.

Then, the pre-given kit of UI components is good for build-out new pages. We do not repeat ourselves and reuse a lot.

The unit test for UI, eirther functional Protractor and so on, or visual with aytomatic screenshort comparisson sound very promissing.

As a result the product is good, visualy consistent, clean coded. People used shared code and company libraries when they are easy to use.

Its helps the whole teem to be at the same page. Literraly. There is a page with components, a designer and a developer are looking at it at the same time and they are seeing the same thing. They both know what is implemented and how exactly it works. Also helps for remote teams, we are trying it right away at our client's.

And, our main goal, the style-guide-driven mindset is much closer. I would not say that we have solved this problem, because this is not about tools, this is about our culture. But with the tools we technically help as much as we can.

## 19. Developers mindset

And the culture we are hoping to develop through this process is so that developers would consider interfaces not as pages but as modular systems.

## 20. Thank you
