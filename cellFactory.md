# How cellFactory works in ListView and TableView

## Code Example 1.1, listview creation with call back 
```java
ListView<T> view = new ListView<>();
ObservableList<String> data = FXCollections.observableArrayList(List<T> objectList);
view.setItems(data);
view.setCellFactory(
  new Callback<ListView<T>, ListCell<T>>() {
    @Override
    public ListCell<T> call(ListView<T> list) {
      return new MyCell();
    }
  }
);
```

## Code Example 1.2, listview creation with lambda function
```java
ListView<T> view = new ListView<>();
ObservableList<String> data = FXCollections.observableArrayList(List<T> objectList);
view.setItems(data);
view.setCellFactory((list) -> {
  Mycell cell = new Mycell();
  return cell;
});
```

## Code Example 2.1, code-defined cells
```java
//cell needs extend ListCell<T>
static class MyCell extends ListCell<T> {
  @Override
  //listener monitoring addition or reduction of items
  public void updateItem(T item, boolean empty) {
    //seems necessart to invoke super()
    super.updateItem(item, empty);
    //customize cells
    Rectangle rect = new Rectangle(30, 20);
    if (item != null) {
      setText("   "+item.toString());
      rect.setFill(Color.web(item));
      //implement the customized cell to listview
      setGraphic(rect);
    }
  }
}
```

## Code Example 2.2, fxml-defined cells
```
static class MyCell extends ListCell<T> {
  @Override
  public void updateItem(String item, boolean empty) {
    super.updateItem(item, empty);
    //read fxml
    FXMLLoader loader = new FXMLLoader();
		loader.setLocation(this.getClass().getResource("cellFormat.fxml"));
    setGraphic(loader.load());
    if (item != null) {
      setGraphic(loader.load());
    }
  }
}
```
