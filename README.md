# Help-FakeRepository
```
public class FakeRepository
{
  private readonly List<Product> list;
  public FakeRepository()
  {
      list = new List<Product>() {
          new Product(new Guid("C56A4180-65AA-42EC-A945-5FD21DEC0537"), "Product A"),
          new Product(new Guid("C56A4180-65AA-42EC-A945-5FD21DEC0538"), "Product B"),
          new Product(new Guid("C56A4180-65AA-42EC-A945-5FD21DEC0539"), "Product C"),
      };
  }

  public bool Exists(string name)
  {
      foreach (var item in list)
      {
          if (name == item.Name)
              return true;
      }

      return false;
  }

  public void Create(Product product)
  {
      list.Add(product);
  }


  public void Delete(Guid id)
  {
      foreach (var item in list)
      {
          if (id == item.Id)
              list.Remove(item);
      }
  }

  public bool Exist(Guid id)
  {
      foreach (var item in list)
      {
          if (id == item.Id)
              return true;
      }

      return false;
  }

  public IEnumerable<Product> GetAll()
  {
      return list;
  }

  public Product GetById(Guid id)
  {
      foreach (var item in list)
      {
          if (id == item.Id)
              return item;
      }

      return null;
  }

  public void Update(Product product)
  {
      foreach (var item in list)
      {
          if (product.Id == item.Id)
          {
              list.Remove(item);
              list.Add(product);
          }

      }
  }
}
```

```
public class Product
{
    public Product(Guid id, string name)
    {
        Id = id;
        Name = name;
    }
    public Product(string name)
    {
        Id = Guid.NewGuid();
        Name = name;
    }

    public Guid Id { get; set; }
    public string Name { get; set; }
}
```` 
