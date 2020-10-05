# How cellFactory works in ListView and TableView
## 
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
```
