---
layout: post 

title: Swift Dynamic Table View  

date: 2018-02-09 15:03:22 

author: C.W.Kim 

categories: Iron

tags: Swift Dynamic TableView 
---
### Swift Dynamic Table View  ### 

```swift
    @IBAction func addAction(_ sender: Any) {
        if let indexPath  = tableView.indexPathForSelectedRow {
            let cell = tableView.cellForRow(at: indexPath ) as! DynamicTableViewCell
            
            let field = UITextField(frame: CGRect(x: 0, y: 0, width: 300 , height: 100 ))
            field.textColor = .blue
            field.backgroundColor = .yellow
            field.text = "Good Morning ~~~~ "
            //print(field.systemLayoutSizeFitting(CGSize(width: 300, height:100 )))
            
           // let cField = cell.dynamicField[0] // cell.dynamicField[0].copy() as! DesignableTextField
            let dField = addField()
            cell.dynamicField.removeAll(keepingCapacity: false)
            cell.dynamicField.append(dField)
            //cell.stackView.addArrangedSubview(field)
            var rowHeight = cell.stackView.frame.height
            for d in cell.dynamicField {
                print("......")
                //d.translatesAutoresizingMaskIntoConstraints = false
               // d.heightAnchor.constraint(equalToConstant: 300).isActive = true
                cell.stackView.addArrangedSubview(d)
                print("height =   \(d.heightAnchor)" )
                rowHeight = rowHeight + 300
                //cell.stackView.addSubview(d)
            }
            //cell?.  //    addSubview(field)
            
            //tableView.estimatedRowHeight = UITableViewAutomaticDimension
            
            //tableView.rowHeight =  cell.stackView.frame.height + 40
            //UITableViewAutomaticDimension
            
            
            data[indexPath.row].2 = rowHeight
            self.tableView.reloadData()
        }
        
    }
    
    
    func addField() -> DesignableTextField {
        // make random and unique Number
        let unique = Date().timeIntervalSince1970.description
        let fieldName = "IR " + unique
        fields.insert(fieldName)
        
        
        let field = DesignableTextField(frame: CGRect(x: 0 , y: 0, width: 300, height: 30))
        
        field.cornerRadius = 5
        field.backgroundColor = .blue
        field.textColor = .white
        field.text = fieldName
        field.textAlignment = .center
        // https://stackoverflow.com/questions/26180822/swift-adding-constraints-programmatically
        //field.addConstraint() -- 9.0 이전 방식
        field.widthAnchor.constraint(equalToConstant: 300).isActive = true
        let heightConstraint = field.heightAnchor.constraint(equalToConstant: 300.0)
        heightConstraint.isActive = true
        print("Height Constraint = \(heightConstraint.constant)")
        return field
    }
```

