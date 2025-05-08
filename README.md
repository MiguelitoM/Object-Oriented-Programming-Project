# 🐾 Animal Hotel Management Project (Object‑Oriented Programming)

## 🔍 Overview
The application is a **Java console program** that manages a veterinary hotel with animals, keepers, veterinarians, habitats, trees and vaccines.  
It stores data, calculates satisfaction indexes and lets the user interact via nested menus. The project features design patterns such as Strategy, State and more.

## Application Menus & Commands
### Main Menu  

| Option | Action |
|--------|--------|
| **Create / Open / Save** | Manage persistent state (Java serialization). |
| **Advance Season** | Move to next season, updating every tree. |
| **Show Global Satisfaction** | Print rounded total satisfaction of all animals **+** staff. |
| **Animals / Employees / Habitats / Vaccines / Look‑ups** | Enter the corresponding management submenu. |
| **Exit** | Leave application (no auto‑save). |

### Animals Menu

- **Show All** – list every animal with health history.  
- **Register** – add a new animal.  
- **Transfer to Habitat** – move an animal.  
- **Show Satisfaction** – print one animal’s satisfaction score.

### Employees Menu

- **Show All** – list vets & keepers with current responsibilities.  
- **Register** – add new employee (choose VET or TRT).  
- **Add Responsibility** – give a vet a species or a keeper a habitat.  
- **Remove Responsibility** – revoke one.  
- **Show Satisfaction** – print employee’s satisfaction score.

### Habitats Menu

- **Show All** – list habitats; optionally expand to show trees.  
- **Register** – create new habitat.  
- **Change Area** – edit size.  
- **Change Influence** – set POS / NEG / NEU for a species.  
- **Add Tree** – plant a tree.  
- **Show Trees** – list every tree in one habitat.

### Vaccines Menu

- **Show All** – list vaccines with number of uses & allowed species.  
- **Register** – create vaccine (checks species ids).  
- **Vaccinate Animal** – ask for vaccine id, vet id, animal id; warns if wrong species.  
- **Show Vaccinations** – global chronological list of administrations.

### Look‑ups Menu

- **Animals in Habitat**  
- **Vaccines of Animal**  
- **Medical Acts by Veterinarian**  
- **Wrong Vaccinations** – all shots that harmed animals.


## 🧪 Testing

```bash
java -Dimport=test.import -Din=test.in -Dout=test.outhyp hva.app.App
diff -b test.out test.outhyp     # no output ⇒ tests pass
```
