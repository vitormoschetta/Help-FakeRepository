# CSharp
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





# TypeScript

```
export class ProductFakeService {
  list: Product[]

  constructor() {
    this.list = [
      { id: '1', name: 'product 01', price: '1.99' },
      { id: '2', name: 'product 02', price: '9.99' },
      { id: '3', name: 'product 03', price: '2.55' },
      { id: '4', name: 'product 04', price: '5.99' },
    ];
  }

  Create(product: Product): void {   
    product.id = (this.list.length + 1).toString()
    this.list.push(product)   
  }

  Update(product: Product): void { 
    let item = this.list.find(x => x.id == product.id)
    item.name = product.name
    item.price = product.price         
  }

  Delete(id: string): void { 
    for(var i=0; i < this.list.length; i++) {
      if (this.list[i].id == id) 
        this.list.splice(i,1)               
    }      
  }

  GetAll(): Product[] {
    return this.OderByName(this.list)
  }

  GetById(id: string): Product {
    return this.list.find(x => x.id == id)
  }  

  Exist(name: string): boolean {
    var item = this.list.find(x => x.name == name)
    if (item == undefined)
      return false
    return true
  }

  existUpdate(name: string, id: string): boolean {
    var item = this.list.find(x => x.name == name && x.id != id)
    if (item == undefined)
      return false
    return true
  }

  OderByName(list: Product[]) {
    return list.sort(function (a, b) {
      if (a.name < b.name) { return -1; }
      if (a.name > b.name) { return 1; }
      return 0;
    })
  }
}
 
```

