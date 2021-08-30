## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/nenadam/test-pages/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block 1

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/nenadam/test-pages/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.

```dart
class BlocApp extends StatelessWidget {
  final TodosInteractor todosInteractor;
  final UserRepository userRepository;

  const BlocApp({
    Key key,
    @required this.todosInteractor,
    @required this.userRepository,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Injector(
      todosInteractor: todosInteractor,
      userRepository: userRepository,
      child: TodosBlocProvider(
        bloc: TodosListBloc(todosInteractor),
        child: MaterialApp(
          onGenerateTitle: (context) => BlocLocalizations.of(context).appTitle,
          theme: ArchSampleTheme.theme,
          localizationsDelegates: [
            ArchSampleLocalizationsDelegate(),
            InheritedWidgetLocalizationsDelegate(),
          ],
          routes: {
            ArchSampleRoutes.home: (context) {
              return HomeScreen(
                repository: Injector.of(context).userRepository,
              );
            },
            ArchSampleRoutes.addTodo: (context) {
              return AddEditScreen(
                addTodo: TodosBlocProvider.of(context).addTodo.add,
              );
            },
          },
        ),
      ),
    );
  }
}
```
