# Help-FakeRepository
```
public class FakeRepository
{
  private readonly List<Product> List;
  public FakeProductRepository()
  {
      List = new List<Product>() {
          new Product("Product A", 5.99m),
          new Product("Product B", 10.00m),
          new Product("Product C", 500.00m)
      };
  }

  public bool Exists(string name)
  {
      var item = List.FirstOrDefault(x => x.Name == name);
      if (item != null)
          return true;

      return false;
  }
  
  public bool ExistsUpdate(string name, Guid id)
  {
      var item = List.FirstOrDefault(x => x.Name == name && x.Id != id);
      if (item != null)
          return true;

      return false;

  }

  public void Create(Product model)
  {
      List.Add(model);
  }


  public void Delete(Guid id)
  {
      var item = List.FirstOrDefault(x => x.Id == id);
      if (item != null)
          List.Remove(item);
  }


  public IEnumerable<Product> GetAll()
  {
      return List;
  }

  public Product GetById(Guid id)
  {
      return List.FirstOrDefault(x => x.Id == id);
  }

  public void Update(Product model)
  {
      var item = List.FirstOrDefault(x => x.Id == model.Id);
      if (item != null)
      {
          List.Remove(item);
          List.Add(model);
      }

  }
  
  public List<Product> Search(string param)
  {
      var lista = List.Where(x => x.Name.Contains(param) || x.Price.ToString().Contains(param)).ToList();
      return lista;
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
