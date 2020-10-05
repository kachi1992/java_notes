# How cellFactory works in ListView and TableView
## Code Example

```java
ListView<T> view = new ListView<>();
ObservableList<String> data = FXCollections.observableArrayList(List<T> object);
view.setItems(data);
view.setCellFactory(
  new Callback<ListView<String>, ListCell<String>>() {
    @Override
    public ListCell<String> call(ListView<String> list) {
      return new MyCell();
    }
  }
);

//cell needs extend ListCell<T>
static class MyCell extends ListCell<T> {
  @Override
  //listener monitoring addition or reduction of items
  public void updateItem(String item, boolean empty) {
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
