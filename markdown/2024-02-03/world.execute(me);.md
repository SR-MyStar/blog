# 手抄`world.execute(me);`的代码并转成Rust

闲来无事，用Rust写了一份`world.execute(me);`(一首带Java代码的歌)的代码

### `main.rs`(主体)

```rust
//! The program `god_drinks_rust` implements an application that
//! creates an empty simulated world with no meaning or purpose.

use god_drinks_rust::*;
use std::any::{Any, TypeId};

fn main() {
    let mut me = Thing::new(Lovable::new("Me", 0, true, -1, false));
    let mut you = Thing::new(Lovable::new("You", 0, true, -1, false));

    let mut world = World::new(5);
    world.add_thing(&mut me);
    world.add_thing(&mut you);
    world.start_simulation();





















    if me.type_id() == TypeId::of::<PointSet>() {
        you.add_attribute(me.dimensions().to_attribute());
        me.reset_dimensions();
    }
    if me.type_id() == TypeId::of::<Circle>() {
        you.add_attribute(me.circumference().to_attribute());
        me.reset_circumference();
    }
    if me.type_id() == TypeId::of::<SineWave>() {
        you.add_action(Action::Sit, me.tangent(you.x_position()));
    }
    if me.type_id() == TypeId::of::<Sequence>() {
        me.set_limit(you.to_limit());
    }




























    me.toggle_current();

    me.can_see(false);
    me.add_feeling(Feel::Dizzy);

    world.time_travel_for_two(Year::AD, 617, &me, &you);
    world.time_travel_for_two(Year::BC, 3691, &me, &you);

    world.unite(&mut me, &mut you);






















    if me.num_stimulations_available() >= you.num_stimulations_needed() {
        you.set_satisfaction(me.to_satisfaction());
    }
    if me.can_make(&you, Feel::Happy) {
        me.request_execution(&mut world);
    }
    world.lock_thing(&me);
    world.lock_thing(&you);






    if me.type_id() == TypeId::of::<Eggplant>() {
        you.add_attribute(me.nutrients().to_attribute());
        me.reset_nutrients();
    }
    if me.type_id() == TypeId::of::<Tomato>() {
        you.add_attribute(me.antioxidants().to_attribute());
        me.reset_antioxidants();
    }
    if me.type_id() == TypeId::of::<TabbyCat>() {
        me.purr();
    }
    if me == world.god {
        me.set_proof(you.to_proof());
    }





    me.toggle_gender();
    world.procreate(&mut me, &mut you);

    me.toggle_role_bdsm();
    world.make_high(&mut me);
    world.make_high(&mut you);







    if me.can_feel_your(Feel::Vibration) {
        me.add_feeling(Feel::Complete);
    }

    world.unlock(&you);
    world.remove_thing(&mut you);
    me.look_for(&you, &mut world);
    me.look_for(&you, &mut world);
    me.look_for(&you, &mut world);
    me.look_for(&you, &mut world);
    me.look_for(&you, &mut world);

    if me.memory().is_erasable() {
        me.remove_feeling(Feel::Disheartened);
    }
    if let Err(IllegalArgumentError) = me.set_opinion(me.opinion_index("you are here"), false) {
        world.announce("God is always true.");
    }












    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.run_execution();
    world.announce_with_locale("1", Locale::De);
    world.announce_with_locale("2", Locale::Es);
    world.announce_with_locale("3", Locale::Fr);
    world.announce_with_locale("4", Locale::Kr);
    world.announce_with_locale("5", Locale::Se);
    world.announce_with_locale("6", Locale::Cn);
    world.run_execution();




    if world.is_executable_by(&me) {
        you.set_execution(me.to_execution());
    }
    if world.get_thing_index(&you).is_some() {
        world.run_execution();
    }
    me.escape(&mut world);




    me.learn_topic(Love::Love);
    me.take_exam_topie(Love::Love);
    me.algebraic_expression(Love::Love);
    me.escape_love(Love::Love);











    world.execute(me);
}
```

### `lib.rs`(只是为了通过编译)

```rust
use std::{fmt, result};

pub struct IllegalArgumentError;
impl fmt::Display for IllegalArgumentError {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "Illegal argument") // user-facing output
    }
}

type Result<T> = result::Result<T, IllegalArgumentError>;

#[derive(Clone, Eq, PartialEq)]
pub struct Thing;
impl Thing {
    pub fn new(_thing: Lovable) -> Self {
        Self
    }
    pub fn dimensions(&self) -> Dimensions {
        Dimensions
    }
    pub fn add_attribute(&mut self, _attribute: Attribute) {}
    pub fn reset_dimensions(&mut self) {}
    pub fn circumference(&self) -> Circumference {
        Circumference
    }
    pub fn reset_circumference(&mut self) {}
    pub fn add_action(&mut self, _action: Action, _tangent: Tangent) {}
    pub fn tangent(&self, _x_position: i8) -> Tangent {
        Tangent
    }
    pub fn x_position(&self) -> i8 {
        0
    }
    pub fn set_limit(&mut self, _limit: f64) {}
    pub fn to_limit(&self) -> f64 {
        f64::INFINITY
    }
    pub fn toggle_current(&mut self) {}
    pub fn can_see(&mut self, _can_see: bool) {}
    pub fn add_feeling(&mut self, _feel: Feel) {}
    pub fn num_stimulations_available(&self) -> usize {
        0
    }
    pub fn num_stimulations_needed(&self) -> usize {
        0
    }
    pub fn set_satisfaction(&mut self, _satisfaction: Satisfaction) {}
    pub fn to_satisfaction(&self) -> Satisfaction {
        Satisfaction
    }
    pub fn can_make(&self, _you: &Thing, _feel: Feel) -> bool {
        true
    }
    pub fn request_execution(&self, _world: &mut World) {}
    pub fn nutrients(&self) -> Nutrients {
        Nutrients
    }
    pub fn reset_nutrients(&mut self) {}
    pub fn antioxidants(&self) -> Antioxidants {
        Antioxidants
    }
    pub fn reset_antioxidants(&mut self) {}
    pub fn purr(&self) {}
    pub fn set_proof(&mut self, _proof: Proof) {}
    pub fn to_proof(&self) -> Proof {
        Proof
    }
    pub fn toggle_gender(&mut self) {}
    pub fn toggle_role_bdsm(&mut self) {}
    pub fn can_feel_your(&self, _feel: Feel) -> bool {
        true
    }
    pub fn look_for(&mut self, _thing: &Thing, _world: &mut World) {}
    pub fn memory(&mut self) -> Memory {
        Memory
    }
    pub fn remove_feeling(&mut self, _feel: Feel) {}
    pub fn set_opinion(&mut self, _opinion_index: usize, _option: bool) -> Result<()> {
        if _opinion_index == 0 {
            Err(IllegalArgumentError)
        } else {
            Ok(())
        }
    }
    pub fn opinion_index(&self, _opinion: &str) -> usize {
        if _opinion == "you are here" {
            0
        } else {
            1
        }
    }
    pub fn set_execution(&mut self, _execution: Execution) {}
    pub fn to_execution(&self) -> Execution {
        Execution
    }
    pub fn escape(&mut self, _world: &mut World) {}
    pub fn learn_topic(&mut self, _topic: Love) {}
    pub fn take_exam_topie(&mut self, _topic: Love) {}
    pub fn algebraic_expression(&self, _expression: Love) {}
    pub fn escape_love(&mut self, _love: Love) {}
}

pub struct Lovable;
impl Lovable {
    pub fn new(_name: &str, _cfg1: i8, _cfg2: bool, _cfg_3: i8, _cfg4: bool) -> Self {
        Self
    }
}

pub struct World {
    pub god: Thing,
}
impl World {
    pub fn new(_cfg1: i8) -> Self {
        Self {
            god: Thing::new(Lovable::new("god", 0, false, 0, false)),
        }
    }
    pub fn add_thing(&mut self, _thing: &mut Thing) {}
    pub fn start_simulation(&mut self) {}
    pub fn time_travel_for_two(
        &mut self,
        _year_flag: Year,
        _year: usize,
        _me: &Thing,
        _you: &Thing,
    ) {
    }
    pub fn unite(&mut self, _me: &mut Thing, _you: &mut Thing) {}
    pub fn lock_thing(&mut self, _thing: &Thing) {}
    pub fn procreate(&mut self, _me: &mut Thing, _you: &mut Thing) {}
    pub fn make_high(&mut self, _thing: &mut Thing) {}
    pub fn unlock(&mut self, _thing: &Thing) {}
    pub fn remove_thing(&mut self, _thing: &mut Thing) {}
    pub fn announce(&mut self, _message: &str) {}
    pub fn run_execution(&mut self) {}
    pub fn announce_with_locale(&mut self, _message: &str, _language: Locale) {}
    pub fn is_executable_by(&self, _thing: &Thing) -> bool {
        true
    }
    pub fn get_thing_index(&self, _thing: &Thing) -> Option<&Thing> {
        None
    }
    pub fn execute(&mut self, _thing: Thing) {}
}

pub struct PointSet;

pub struct Dimensions;
impl ToAttribute for Dimensions {}

pub trait ToAttribute {
    fn to_attribute(&self) -> Attribute {
        Attribute
    }
}

pub struct Attribute;

pub struct Circle;

pub struct Circumference;
impl ToAttribute for Circumference {}

pub struct SineWave;

pub struct Tangent;

pub struct Sequence;

pub enum Year {
    AD,
    BC,
}

pub enum Action {
    Sit,
}

pub enum Feel {
    Dizzy,
    Happy,
    Vibration,
    Complete,
    Disheartened,
}

pub struct Satisfaction;

pub struct FeelStruct {
    pub happy: bool,
}

pub struct Eggplant;

pub struct Nutrients;
impl ToAttribute for Nutrients {}

pub struct Tomato;

pub struct Antioxidants;
impl ToAttribute for Antioxidants {}

pub struct TabbyCat;

pub struct Proof;

pub struct Memory;
impl Memory {
    pub fn is_erasable(&self) -> bool {
        false
    }
}

pub enum Locale {
    De,
    Es,
    Fr,
    Kr,
    Se,
    Cn,
}

pub struct Execution;

pub enum Love {
    Love,
}
```
