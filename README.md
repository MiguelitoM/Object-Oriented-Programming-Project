# 🐾 Animal Hotel Management Project (Object‑Oriented Programming)

## ✨ What You’re Building
The application is a **Java console program** that manages a veterinary hotel with animals, keepers, veterinarians, habitats, trees and vaccines.  
It stores data, calculates satisfaction indexes and lets the user interact via nested menus backed by a persistent file format.

---

## 1  Domain Model (high‑level)

| Section | Purpose |
|---------|---------|
| **Species** | Unique key + unique name; keeps its animals. |
| **Animals** | Unique id, name, species, health log, current habitat; satisfaction depends on companions, habitat area & suitability. |
| **Habitats** | Unique id, name, area, trees, resident animals; can influence species positively, negatively or neutrally. |
| **Trees** | Unique id, name, age, base cleaning difficulty, type (DECIDUOUS / EVERGREEN); seasonal cleaning effort affects keeper workload. |
| **Employees** | Two kinds:<br>**TRT** (keepers) responsible for habitats;<br>**VET** (vets) responsible for species they can vaccinate. |
| **Vaccines** | Unique id, name, list of allowed species; stores every administration record. |

Satisfaction formulas exist for animals, vets and keepers, but you do **not** need to memorise them now—the core is already scaffolded for you.

---

## 2  Application Menus & Commands

### 2.1 Main Menu  
(*labels provided by `hva.app.main.*`*)

| Option | Action |
|--------|--------|
| **Create / Open / Save** | Manage persistent state (Java serialization). |
| **Advance Season** | Move to next season, updating every tree. |
| **Show Global Satisfaction** | Print rounded total satisfaction of all animals **+** staff. |
| **Animals / Employees / Habitats / Vaccines / Look‑ups** | Enter the corresponding management submenu. |
| **Exit** | Leave application (no auto‑save). |

### 2.2 Animals Menu

- **Show All** – list every animal with health history.  
- **Register** – add a new animal (creates species on the fly if unknown).  
- **Transfer to Habitat** – move an animal.  
- **Show Satisfaction** – print one animal’s satisfaction score.

### 2.3 Employees Menu

- **Show All** – list vets & keepers with current responsibilities.  
- **Register** – add new employee (choose VET or TRT).  
- **Add Responsibility** – give a vet a species or a keeper a habitat.  
- **Remove Responsibility** – revoke one.  
- **Show Satisfaction** – print employee’s satisfaction score.

### 2.4 Habitats Menu

- **Show All** – list habitats; optionally expand to show trees.  
- **Register** – create new habitat.  
- **Change Area** – edit size.  
- **Change Influence** – set POS / NEG / NEU for a species.  
- **Add Tree** – plant a tree (DECIDUOUS or EVERGREEN).  
- **Show Trees** – list every tree in one habitat.

### 2.5 Vaccines Menu

- **Show All** – list vaccines with number of uses & allowed species.  
- **Register** – create vaccine (checks species ids).  
- **Vaccinate Animal** – ask for vaccine id, vet id, animal id; warns if wrong species.  
- **Show Vaccinations** – global chronological list of administrations.

### 2.6 Look‑ups Menu

- **Animals in Habitat**  
- **Vaccines of Animal**  
- **Medical Acts by Veterinarian**  
- **Wrong Vaccinations** – all shots that harmed animals.

---

## 3  Text File Bootstrap

At launch you may preload data with

```bash
java -Dimport=initial.import hva.app.App
```

The importer understands lines like  
`ANIMAL|A1|Alex|C10|AR1` or `HABITAT|AR2|Tropical Forest|30|T1,T4`.

---

## 4  Running the Public Tests

Compile once with Maven/IDE or simply run:

```bash
java -Dimport=test.import -Din=test.in -Dout=test.outhyp hva.app.App
diff -b test.out test.outhyp     # no output ⇒ tests pass
```

`-Dimport` provides initial objects, `-Din` the scripted user input,  
`-Dout` is where your program must write its answers.

---

## 5  Design Expectations

* Open/Closed principle – new employee types or satisfaction strategies should plug‑in, not rewrite code.  
* Apply suitable design patterns for trees’ season behaviour and employee satisfaction policies.  
* Core logic lives in **`hva-core`**; UI strings live in **`hva-app`**; never mix them.

That’s it—focus on completing the missing classes and methods, keeping to the provided interfaces and menu flow. Good luck!
