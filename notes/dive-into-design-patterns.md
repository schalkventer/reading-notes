Dive Into Design Patterns (2018)

Alexander Shvets

───────────────

▪ Design pat­terns are uni­ver­sal. There­fore, all code sam­ples in this book are writ­ten in pseudocode that doesn’t con­strain the mate­r­i­al to a par­tic­u­lar pro­gram­ming language

▪ Prior to study­ing pat­terns, you can refresh your mem­o­ry by going over the key terms of object-ori­ent­ed pro­gram­ming

▪ That chap­ter also explains the basics of UML dia­grams, which is use­ful because the book has tons of them.

▪ Object-orient­ed program­ming is a par­a­digm based on the con­cept of wrap­ping pieces of data, and behav­ior relat­ed to that data, into spe­cial bun­dles called objects, which are con­struct­ed from a set of “blue­prints”, defined by a pro­gram­mer, called class­es.

▪ Say you have a cat named Oscar. Oscar is an object, an instance of the Cat class. Every cat has a lot of stan­dard attrib­ut­es: name, sex, age, weight, color, favorite food, etc. These are the class’s fields.

▪ All cats also behave sim­i­lar­ly: they breathe, eat, run, sleep and meow. These are the class’s meth­ods. Col­lec­tive­ly, fields and meth­ods can be ref­er­enced as the mem­bers of their class.

▪ Data stored inside the object’s fields is often ref­er­enced as state, and all the object’s meth­ods define its behav­ior.

▪ Nat­u­ral­ly, a real pro­gram con­tains more than a sin­gle class. Some of these class­es might be orga­nized into class hier­ar­chies.

▪ A par­ent class, like the one we’ve just defined, is called a super­class. Its chil­dren are sub­class­es. Sub­class­es inher­it state and behav­ior from their par­ent, defin­ing only attrib­ut­es or behav­iors that dif­fer.

▪ Such a pyra­mid of class­es is a hier­ar­chy. In such a hier­ar­chy, the Cat class inher­its every­thing from both the Animal and Organism classes.

▪ Class­es in a UML dia­gram can be sim­pli­fied if it’s more impor­tant to show their rela­tions than their contents

▪ Sub­class­es can over­ride the behav­ior of meth­ods that they inher­it from par­ent class­es.

▪ A sub­class can either com­plete­ly replace the default behav­ior or just enhance it with some extra stuff.

▪ Object-ori­ent­ed pro­gram­ming is based on four pil­lars, con­cepts that dif­fer­en­ti­ate it from other pro­gram­ming paradigms.

▪ Most of the time when you’re cre­at­ing a pro­gram with OOP, you shape objects of the pro­gram based on real-world objects

▪ How­ev­er, objects of the pro­gram don’t rep­re­sent the orig­i­nals with 100% accu­ra­cy (and it’s rarely required that they do). Instead, your objects only model attrib­ut­es and behav­iors of real objects in a spe­cif­ic con­text, ignor­ing the rest.

▪ For exam­ple, an Airplane class could prob­a­bly exist in both a flight sim­u­la­tor and a flight book­ing appli­ca­tion. But in the for­mer case, it would hold details relat­ed to the actu­al flight, where­as in the lat­ter class you would care only about the seat map and which seats are available

▪ Abstrac­tion is a model of a real-world object or phe­nom­e­non, lim­it­ed to a spe­cif­ic con­text, which rep­re­sents all details rel­e­vant to this con­text with high accu­ra­cy and omits all the rest.

▪ To start a car engine, you only need to turn a key or press a but­ton. You don’t need to con­nect wires under the hood, rotate the crank­shaft and cylin­ders, and ini­ti­ate the power cycle of the engine. These details are hid­den under the hood of the car. You have only a sim­ple inter­face: a start switch, a steer­ing wheel and some ped­als. This illus­trates how each object has an inter­face—a pub­lic part of an object, open to inter­ac­tions with other objects.

▪ Encap­su­la­tion is the abil­i­ty of an object to hide parts of its state and behav­iors from other objects, expos­ing only a lim­it­ed inter­face to the rest of the program

▪ To encap­su­late some­thing means to make it private, and thus acces­si­ble only from with­in the meth­ods of its own class. There’s a lit­tle bit less restric­tive mode called protected that makes a mem­ber of a class avail­able to sub­class­es as well.

▪ Inter­faces and abstract class­es/meth­ods of most pro­gram­ming lan­guages are based on the con­cepts of abstrac­tion and encap­su­la­tion

▪ In mod­ern object-ori­ent­ed pro­gram­ming lan­guages, the inter­face mech­a­nism (usu­al­ly declared with the interface or protocol key­word) lets you define con­tracts of inter­ac­tion between objects.

▪ That’s one of the rea­sons why the inter­faces only care about behav­iors of objects, and why you can’t declare a field in an interface.

▪ The fact that the word inter­face stands for a pub­lic part of an object, while there’s also the interface type in most pro­gram­ming lan­guages, is very con­fus­ing. I’m with you on that.

▪ Imag­ine that you have a FlyingTransport inter­face with a method fly(origin, destination, passengers)
. When design­ing an air trans­porta­tion sim­u­la­tor, you could restrict the Airport class to work only with objects that imple­ment the FlyingTransport inter­face

▪ After this, you can be sure that any object passed to an air­port object, whether it’s an Airplane, a Helicopter or a freak­ing DomesticatedGryphon would be able to arrive or depart from this type of airport.

▪ You could change the imple­men­ta­tion of the fly method in these class­es in any way you want. As long as the sig­na­ture of the method remains the same as declared in the inter­face, all instances of the Airport class can work with your fly­ing objects just fine.

▪ Inher­i­tance is the abil­i­ty to build new class­es on top of exist­ing ones. The main ben­e­fit of inher­i­tance is code reuse

▪ The con­se­quence of using inher­i­tance is that sub­class­es have the same inter­face as their par­ent class. You can’t hide a method in a sub­class if it was declared in the super­class. You must also imple­ment all abstract meth­ods, even if they don’t make sense for your subclass.

▪ UML dia­gram of extend­ing a sin­gle class ver­sus imple­ment­ing mul­ti­ple inter­faces at the same time.

▪ In most pro­gram­ming lan­guages a sub­class can extend only one super­class. On the other hand, any class can imple­ment sev­er­al inter­faces at the same time

▪ But, as I men­tioned before, if a super­class imple­ments an inter­face, all of its sub­class­es must also imple­ment it.

▪ Most Animals can make sounds. We can antic­i­pate that all sub­class­es will need to over­ride the base makeSound method so each sub­class can emit the cor­rect sound; there­fore we can declare it abstract right away. This lets us omit any default imple­men­ta­tion of the method in the super­class, but force all sub­class­es to come up with their own.

▪ Imag­ine that we’ve put sev­er­al cats and dogs into a large bag. Then, with closed eyes, we take the ani­mals one-by-one out of the bag. After tak­ing an ani­mal from the bag, we don’t know for sure what it is.

▪ How­ev­er, if we cud­dle it hard enough, the ani­mal will emit a spe­cif­ic sound of joy, depend­ing on its con­crete class.

▪ bag = [new Cat(), new Dog()];

foreach (Animal a : bag)
  a.makeSound()

// Meow!
// Woof!

▪ The pro­gram doesn’t know the con­crete type of the object con­tained inside the a vari­able; but, thanks to the spe­cial mech­a­nism called poly­mor­phism, the pro­gram can trace down the sub­class of the object whose method is being exe­cut­ed and run the appro­pri­ate behavior

▪ Poly­mor­phism is the abil­i­ty of a pro­gram to detect the real class of an object and call its imple­men­ta­tion even when its real type is unknown in the cur­rent context.

▪ You can also think of poly­mor­phism as the abil­i­ty of an object to “pre­tend” to be some­thing else, usu­al­ly a class it extends or an inter­face it imple­ments. In our exam­ple, the dogs and cats in the bag were pre­tend­ing to be gener­ic animals.

▪ In addi­tion to inher­i­tance and imple­men­ta­tion that we’ve already seen, there are other types of rela­tions between objects that we haven’t talked about yet.

▪ Depen­den­cy is the most basic and the weak­est type of rela­tions between class­es

▪ There is a depen­den­cy between two class­es if some changes to the def­i­n­i­tion of one class might result in mod­i­fi­ca­tions to anoth­er class.

▪ Depen­den­cy typ­i­cal­ly occurs when you use con­crete class names in your code. For exam­ple, when spec­i­fy­ing types in method sig­na­tures, when instan­ti­at­ing objects via con­struc­tor calls, etc.

▪ You can make a depen­den­cy weak­er if you make your code depen­dent on inter­faces or abstract class­es instead of con­crete classes.

▪ Usu­al­ly, a UML dia­gram doesn’t show every depen­den­cy—there are far too many of them in any real code. Instead of pol­lut­ing the dia­gram with depen­den­cies, you should be very selec­tive and show only those that are impor­tant to what­ev­er it is you are com­mu­ni­cat­ing.

▪ Asso­ci­a­tion is a rela­tion­ship in which one object uses or inter­acts with anoth­er

▪ In UML dia­grams, the asso­ci­a­tion rela­tion­ship is shown by a sim­ple arrow drawn from an object and point­ing to the object it uses.

▪ By the way, hav­ing a bi-direc­tion­al asso­ci­a­tion is a com­plete­ly nor­mal thing. In this case, the arrow has a point at each end.

▪ Take a look at the teach method. It takes an argu­ment of the Course class, which is then used in the body of the method. If some­one changes the sig­na­ture of the getKnowledge method (alters its name, or adds some required para­me­ters, etc.) our code will break. That’s why we can say that the Professor class depends on the Course class.

▪ Now, look at the student field and how it’s used in the teach method. We can say for sure that the Student class is anoth­er depen­den­cy for the Professor: if the sig­na­ture of the method remember changes, the Professor’s code will break

▪ How­ev­er, since the student field is always acces­si­ble to any method of the Professor, the Student class is not mere­ly a depen­den­cy, but also an association.

▪ Aggre­ga­tion is a spe­cial­ized type of asso­ci­a­tion that rep­re­sents “one-to-many”, “many-to-many” or “whole-part” rela­tions between mul­ti­ple objects.

▪ Usu­al­ly, under aggre­ga­tion, an object “has” a set of other objects and serves as a con­tain­er or col­lec­tion

▪ The com­po­nent can exist with­out the con­tain­er and can be linked to sev­er­al con­tain­ers at the same time

▪ In UML the aggre­ga­tion rela­tion­ship is shown by a line with an empty dia­mond at the con­tain­er end and an arrow at the end point­ing toward the component.

▪ While we talk about rela­tions between objects, keep in mind that UML rep­re­sents rela­tions between class­es. It means that a uni­ver­si­ty object might con­sist of mul­ti­ple depart­ments even though you see just one “block” for each enti­ty in the dia­gram.

▪ UML nota­tion can rep­re­sent quan­ti­ties on both sides of rela­tion­ships, but it’s okay to omit them if the quan­ti­ties are clear from the context.

▪ Com­po­si­tion is a spe­cif­ic kind of aggre­ga­tion, where one object is com­posed of one or more instances of the other

▪ In UML the com­po­si­tion rela­tion­ship is drawn the same as for aggre­ga­tion, but with a filled dia­mond at the arrow’s base.

▪ Note that many peo­ple often use the term “com­po­si­tion” when they real­ly mean both the aggre­ga­tion and com­po­si­tion. The most noto­ri­ous exam­ple for this is the famous prin­ci­ple “choose com­po­si­tion over inher­i­tance.” It’s not because peo­ple are igno­rant about the dif­fer­ence, but rather because the word “com­po­si­tion” (e.g. “object com­po­si­tion”) sounds more nat­ur­al in the Eng­lish language.

▪ Depen­den­cy: Class А can be affect­ed by changes in class B.

▪ Asso­ci­a­tion: Object А knows about object B. Class A depends on B.

▪ Aggre­ga­tion: Object А knows about object B, and con­sists of B. Class A depends on B.

▪ Com­po­si­tion: Object А knows about object B, con­sists of B, and man­ages B’s life cycle. Class A depends on B.

▪ Imple­men­ta­tion: Class А defines meth­ods declared in inter­face B. Objects A can be treat­ed as B. Class A depends on B.

▪ Inher­i­tance: Class А inher­its inter­face and imple­men­ta­tion of class B but can extend it. Objects A can be treat­ed as B. Class A depends on B.

▪ Rela­tions between objects and class­es: from weak­est to strongest.

▪ Design pat­terns are typ­i­cal solu­tions to com­mon­ly occur­ring prob­lems in soft­ware design.

▪ You can’t just find a pat­tern and copy it into your pro­gram, the way you can with off-the-shelf func­tions or libraries

▪ Pat­terns are often con­fused with algo­rithms, because both con­cepts describe typ­i­cal solu­tions to some known prob­lems

▪ While an algo­rithm always defines a clear set of actions that can achieve some goal, a pat­tern is a more high-level descrip­tion of a solu­tion

▪ The code of the same pat­tern applied to two dif­fer­ent pro­grams may be different.

▪ Most pat­terns are described very for­mal­ly so peo­ple can repro­duce them in many con­texts.

▪ Here are the sec­tions that are usu­al­ly present in a pat­tern description:

▪ Intent of the pat­tern briefly describes both the prob­lem and the solution.

▪ Moti­va­tion fur­ther explains the prob­lem and the solu­tion the pat­tern makes possible.

▪ Struc­ture of class­es shows each part of the pat­tern and how they are related.

▪ Code exam­ple in one of the pop­u­lar pro­gram­ming lan­guages makes it eas­i­er to grasp the idea behind the pattern.

▪ Design pat­terns dif­fer by their com­plex­i­ty, level of detail and scale of applic­a­bil­i­ty to the entire sys­tem being designed

▪ The most basic and low-level pat­terns are often called idioms. They usu­al­ly apply only to a sin­gle pro­gram­ming language.

▪ The most uni­ver­sal and high-level pat­terns are archi­tec­tur­al pat­terns. Devel­op­ers can imple­ment these pat­terns in vir­tu­al­ly any lan­guage. Unlike other pat­terns, they can be used to design the archi­tec­ture of an entire application.

▪ In addi­tion, all pat­terns can be cat­e­go­rized by their intent, or pur­pose. This book cov­ers three main groups of patterns:

▪ Cre­ation­al pat­terns pro­vide object cre­ation mech­a­nisms that increase flex­i­bil­i­ty and reuse of exist­ing code.

▪ Struc­tur­al pat­terns explain how to assem­ble objects and class­es into larg­er struc­tures, while keep­ing these struc­tures flex­i­ble and efficient.

▪ Behav­ioral pat­terns take care of effec­tive com­mu­ni­ca­tion and the assign­ment of respon­si­bil­i­ties between objects.

▪ The con­cept of pat­terns was first described by Christo­pher Alexan­der in A Pat­tern Lan­guage: Towns, Build­ings, Con­struc­tion 3

▪ The book describes a “lan­guage” for design­ing the urban envi­ron­ment. The units of this lan­guage are pat­terns. They may describe how high win­dows should be, how many lev­els a build­ing should have, how large green areas in a neigh­bor­hood are sup­posed to be, and so on.

▪ The idea was picked up by four authors: Erich Gamma, John Vlis­sides, Ralph John­son, and Richard Helm. In 1994, they pub­lished Design Pat­terns: Ele­ments of Reusable Object-Ori­ent­ed Soft­ware 4, in which they applied the con­cept of design pat­terns to pro­gram­ming.

▪ Due to its lengthy name, peo­ple start­ed to call it “the book by the gang of four” which was soon short­ened to sim­ply “the GoF book”.

▪ The “pat­tern approach” became very pop­u­lar in other pro­gram­ming fields, so lots of other pat­terns now exist out­side of object-ori­ent­ed design as well.

▪ The truth is that you might man­age to work as a pro­gram­mer for many years with­out know­ing about a sin­gle pat­tern. A lot of peo­ple do just that

▪ Even in that case, though, you might be imple­ment­ing some pat­terns with­out even know­ing it.

▪ Design pat­terns are a toolk­it of tried and test­ed solu­tions to com­mon prob­lems in soft­ware design. Even if you never encounter these prob­lems, know­ing pat­terns is still use­ful because it teach­es you how to solve all sorts of prob­lems using prin­ci­ples of object-ori­ent­ed design.

▪ Design pat­terns define a com­mon lan­guage that you and your team­mates can use to com­mu­ni­cate more effi­cient­ly.

▪ The idea looks great on paper, but it turns out that mak­ing exist­ing code work in a new con­text usu­al­ly takes extra effort. Tight cou­pling between com­po­nents, depen­den­cies on con­crete class­es instead of inter­faces, hard­cod­ed oper­a­tions—all of this reduces flex­i­bil­i­ty of the code and makes it hard­er to reuse it.

▪ Using design pat­terns is one way to increase flex­i­bil­i­ty of soft­ware com­po­nents and make them eas­i­er to reuse. How­ev­er, this some­times comes at the price of mak­ing the com­po­nents more complicated.

▪ Here’s a piece of wis­dom from Erich Gamma 5, one of the found­ing fathers of design pat­terns, about the role of design pat­terns in code reuse:

I see three lev­els of reuse.

▪ At the low­est level, you reuse class­es: class libraries, con­tain­ers, maybe some class “teams” like con­tain­er/iter­a­tor.

▪ Frame­works are at the high­est level. They real­ly try to dis­till your design deci­sions. They iden­ti­fy the key abstrac­tions for solv­ing a prob­lem, rep­re­sent them by class­es and define rela­tion­ships between them.

▪ JUnit is a small frame­work, for exam­ple. It is the “Hello, world” of frame­works. It has Test, TestCase, TestSuite and rela­tion­ships defined.

▪ A frame­work is typ­i­cal­ly larg­er-grained than just a sin­gle class. Also, you hook into frame­works by sub­class­ing some­where. They use the so-called Hol­ly­wood prin­ci­ple of “don’t call us, we’ll call you.” The frame­work lets you define your cus­tom behav­ior, and it will call you when it’s your turn to do some­thing.

▪ There also is a mid­dle level. This is where I see pat­terns. Design pat­terns are both small­er and more abstract than frame­works. They’re real­ly a descrip­tion about how a cou­ple of class­es can relate to and inter­act with each other.

▪ Change is the only con­stant thing in a pro­gram­mer’s life.

You released a video game for Win­dows, but now peo­ple ask for a macOS version.
You cre­at­ed a GUI frame­work with square but­tons, but sev­er­al months later round but­tons become a trend.
You designed a bril­liant e-com­merce web­site archi­tec­ture, but just a month later cus­tomers ask for a fea­ture that would let them accept phone orders.

▪ First, we under­stand the prob­lem bet­ter once we start to solve it. Often by the time you fin­ish the first ver­sion of an app, you’re ready to rewrite it from scratch because now you under­stand many aspects of the prob­lem much bet­ter. You have also grown pro­fes­sion­al­ly, and your own code now looks like crap.

▪ Some­thing beyond your con­trol has changed. This is why so many dev teams pivot from their orig­i­nal ideas into some­thing new. Every­one who relied on Flash in an online appli­ca­tion has been rework­ing or migrat­ing their code as brows­er after brows­er drops sup­port for Flash.

▪ The third rea­son is that the goal­posts move. Your client was delight­ed with the cur­rent ver­sion of the appli­ca­tion, but now sees eleven “lit­tle” changes he’d like so it can do other things he never men­tioned in the orig­i­nal plan­ning ses­sions. These aren’t friv­o­lous changes: your excel­lent first ver­sion has shown him that even more is possible.

▪ That’s why all sea­soned devel­op­ers try to pro­vide for pos­si­ble future changes when design­ing an appli­ca­tion’s architecture.

▪ What is good soft­ware design? How would you mea­sure it? What prac­tices would you need to fol­low to achieve it? How can you make your archi­tec­ture flex­i­ble, sta­ble and easy to under­stand?

These are the great ques­tions; but, unfor­tu­nate­ly, the answers are dif­fer­ent depend­ing on the type of appli­ca­tion you’re build­ing.

▪ Nev­er­the­less, there are sev­er­al uni­ver­sal prin­ci­ples of soft­ware design that might help you answer these ques­tions for your own project.

▪ Iden­ti­fy the aspects of your appli­ca­tion that vary and sep­a­rate them from what stays the same.

The main goal of this prin­ci­ple is to min­i­mize the effect caused by changes.

▪ In the same way, you can iso­late the parts of the pro­gram that vary in inde­pen­dent mod­ules, pro­tect­ing the rest of the code from adverse effects.

▪ Encap­su­la­tion on a method level

▪ Tax-relat­ed changes become iso­lat­ed inside a sin­gle method. More­over, if the tax cal­cu­la­tion logic becomes too com­pli­cat­ed, it’s now eas­i­er to move it to a sep­a­rate class.

▪ Program to an Interface, not an Implementation

▪ Pro­gram to an inter­face, not an imple­men­ta­tion. Depend on abstrac­tions, not on con­crete classes.

▪ You can tell that the design is flex­i­ble enough if you can eas­i­ly extend it with­out break­ing any exist­ing code

▪ Before and after extract­ing the inter­face. The code on the right is more flex­i­ble than the code on the left, but it’s also more complicated.

▪ After mak­ing this change, you won’t prob­a­bly feel any imme­di­ate ben­e­fit. On the con­trary, the code has become more com­pli­cat­ed than it was before. How­ev­er, if you feel that this might be a good exten­sion point for some extra func­tion­al­i­ty, or that some other peo­ple who use your code might want to extend it here, then go for it.

▪ After doing that, we can apply poly­mor­phism inside the Company class, treat­ing var­i­ous employ­ee objects via the Employee interface.

▪ To solve this prob­lem, we could declare the method for get­ting employ­ees as abstract. Each con­crete com­pa­ny will imple­ment this method dif­fer­ent­ly, cre­at­ing only those employ­ees that it needs.

▪ By the way, you’ve just seen apply­ing a design pat­tern in action! That was an exam­ple of the Fac­to­ry Method pat­tern. Don’t worry: we’ll dis­cuss it later in detail.

▪ Inher­i­tance is prob­a­bly the most obvi­ous and easy way of reusing code between class­es. You have two class­es with the same code. Cre­ate a com­mon base class for these two and move the sim­i­lar code into it. Piece of cake!

▪ Unfor­tu­nate­ly, inher­i­tance comes with caveats that often become appar­ent only after your pro­gram already has tons of class­es and chang­ing any­thing is pret­ty hard.

▪ A sub­class can’t reduce the inter­face of the super­class. You have to imple­ment all abstract meth­ods of the par­ent class even if you won’t be using them.

▪ When over­rid­ing meth­ods you need to make sure that the new behav­ior is com­pat­i­ble with the base one. It’s impor­tant because objects of the sub­class may be passed to any code that expects objects of the super­class and you don’t want that code to break.

▪ Inher­i­tance breaks encap­su­la­tion of the super­class because the inter­nal details of the par­ent class become avail­able to the sub­class. There might be an oppo­site sit­u­a­tion where a pro­gram­mer makes a super­class aware of some details of sub­class­es for the sake of mak­ing fur­ther exten­sion easier.

▪ Sub­class­es are tight­ly cou­pled to super­class­es. Any change in a super­class may break the func­tion­al­i­ty of subclasses

▪ Try­ing to reuse code through inher­i­tance can lead to cre­at­ing par­al­lel inher­i­tance hier­ar­chies. Inher­i­tance usu­al­ly takes place in a sin­gle dimen­sion. But when­ev­er there are two or more dimen­sions, you have to cre­ate lots of class com­bi­na­tions, bloat­ing the class hier­ar­chy to a ridicu­lous size

▪ There’s an alter­na­tive to inher­i­tance called com­po­si­tion. Where­as inher­i­tance rep­re­sents the “is a” rela­tion­ship between class­es (a car is a trans­port), com­po­si­tion rep­re­sents the “has a” rela­tion­ship (a car has an engine).

▪ I should men­tion that this prin­ci­ple also applies to aggre­ga­tion—a more relaxed vari­ant of com­po­si­tion where one object may have a ref­er­ence to the other one but doesn’t man­age its life­cy­cle. Here’s an exam­ple: a car has a dri­ver, but he or she may use anoth­er car or just walk with­out the car.

▪ INHER­I­TANCE: extend­ing a class in sev­er­al dimen­sions (cargo type × engine type × nav­i­ga­tion type) may lead to a com­bi­na­to­r­i­al explo­sion of subclasses.

▪ You can solve this prob­lem with com­po­si­tion. Instead of car objects imple­ment­ing a behav­ior on their own, they can del­e­gate it to other objects.

▪ This struc­ture of class­es resem­bles the Strat­e­gy pat­tern, which we’ll go over later in this book.

▪ SOLID is a mnemon­ic for five design prin­ci­ples intend­ed to make soft­ware designs more under­stand­able, flex­i­ble and maintainable.

▪ As with every­thing in life, using these prin­ci­ples mind­less­ly can cause more harm than good. The cost of apply­ing these prin­ci­ples into a pro­gram’s archi­tec­ture might be mak­ing it more com­pli­cat­ed than it should be

▪ Striv­ing for these prin­ci­ples is good, but always try to be prag­mat­ic and don’t take every­thing writ­ten here as dogma.

▪ Single Responsibility Principle 

A class should have just one rea­son to change.

Try to make every class respon­si­ble for a sin­gle part of the func­tion­al­i­ty pro­vid­ed by the soft­ware, and make that respon­si­bil­i­ty entire­ly encap­su­lat­ed by (you can also say hid­den with­in) the class.

▪ The real prob­lems emerge when your pro­gram con­stant­ly grows and changes. At some point class­es become so big that you can no longer remem­ber their details. Code nav­i­ga­tion slows down to a crawl, and you have to scan through whole class­es or even an entire pro­gram to find spe­cif­ic things.

▪ The num­ber of enti­ties in pro­gram over­flows your brain stack, and you feel that you’re los­ing con­trol over the code.

▪ There’s more: if a class does too many things, you have to change it every time one of these things changes. While doing that, you’re risk­ing break­ing other parts of the class which you didn’t even intend to change.

▪ If you feel that it’s becom­ing hard to focus on spe­cif­ic aspects of the pro­gram one at a time, remem­ber the sin­gle respon­si­bil­i­ty prin­ci­ple and check whether it’s time to divide some class­es into parts.

▪ Open/Closed Principle 

Class­es should be open for exten­sion but closed for modification.

▪ The main idea of this prin­ci­ple is to keep exist­ing code from break­ing when you imple­ment new features.

▪ When I first learned about this prin­ci­ple, I was con­fused because the words open & closed sound mutu­al­ly exclu­sive. But in terms of this prin­ci­ple, a class can be both open (for exten­sion) and closed (for mod­i­fi­ca­tion) at the same time.

▪ If a class is already devel­oped, test­ed, reviewed, and includ­ed in some frame­work or oth­er­wise used in an app, try­ing to mess with its code is risky. Instead of chang­ing the code of the class direct­ly, you can cre­ate a sub­class and over­ride parts of the orig­i­nal class that you want to behave dif­fer­ent­ly. You’ll achieve your goal but also won’t break any exist­ing clients of the orig­i­nal class.

▪ You can solve the prob­lem by apply­ing the Strat­e­gy pat­tern. Start by extract­ing ship­ping meth­ods into sep­a­rate class­es with a com­mon interface.

▪ Now when you need to imple­ment a new ship­ping method, you can derive a new class from the Shipping inter­face with­out touch­ing any of the Order class’ code. The client code of the Order class will link orders with a ship­ping object of the new class when­ev­er the user selects this ship­ping meth­ods in the UI.

▪ As a bonus, this solu­tion let you move the deliv­ery time cal­cu­la­tion to more rel­e­vant class­es, accord­ing to the sin­gle respon­si­bil­i­ty prin­ci­ple.

▪ When extend­ing a class, remem­ber that you should be able to pass objects of the sub­class in place of objects of the par­ent class with­out break­ing the client code.

▪ Para­me­ter types in a method of a sub­class should match or be more abstract than para­me­ter types in the method of the super­class.

▪ Say you cre­at­ed a sub­class that over­rode the method so that it can feed any ani­mal (a super­class of cats): feed(Animal c)
. Now if you pass an object of this sub­class instead of an object of the super­class to the client code, every­thing would still work fine.

▪ The return type in a method of a sub­class should match or be a sub­type of the return type in the method of the super­class. As you can see, require­ments for a return type are inverse to require­ments for para­me­ter types.

▪ Anoth­er anti-exam­ple comes from the world of pro­gram­ming lan­guages with dynam­ic typ­ing: the base method returns a string, but the over­rid­den method returns a number.

▪ A sub­class shouldn’t strength­en pre-con­di­tions. For exam­ple, the base method has a para­me­ter with type int. If a sub­class over­rides this method and requires that the value of an argu­ment passed to the method should be pos­i­tive (by throw­ing an excep­tion if the value is neg­a­tive), this strength­ens the pre-con­di­tions. The client code, which used to work fine when pass­ing neg­a­tive num­bers into the method, now breaks if it starts work­ing with an object of this subclass.

▪ For exam­ple, invari­ants of a cat are hav­ing four legs, a tail, abil­i­ty to meow, etc. The con­fus­ing part about invari­ants is that while they can be defined explic­it­ly in the form of inter­face con­tracts or a set of asser­tions with­in meth­ods, they could also be implied by cer­tain unit tests and expec­ta­tions of the client code.

The rule on invari­ants is the eas­i­est to vio­late because you might mis­un­der­stand or not real­ize all of the invari­ants of a com­plex class. There­fore, the safest way to extend a class is to intro­duce new fields and meth­ods, and not mess with any exist­ing mem­bers of the super­class. Of course, that’s not always doable in real life

▪ A sub­class shouldn’t change val­ues of pri­vate fields of the super­class. What? How’s that even pos­si­ble? It turns out some pro­gram­ming lan­guages let you access pri­vate mem­bers of a class via reflec­tion mech­a­nisms. Other lan­guages (Python, JavaScript) don’t have any pro­tec­tion for the pri­vate mem­bers at all.

▪ This means that the client code will break if we don’t check the doc­u­ment type before sav­ing it.

▪ The result­ing code also vio­lates the open/closed prin­ci­ple, since the client code becomes depen­dent on con­crete class­es of doc­u­ments. If you intro­duce a new doc­u­ment sub­class, you’ll need to change the client code to sup­port it.

▪ You can solve the prob­lem by redesign­ing the class hier­ar­chy: a sub­class should extend the behav­ior of a super­class, there­fore the read-only doc­u­ment becomes the base class of the hier­ar­chy. The writable doc­u­ment is now a sub­class which extends the base class and adds the sav­ing behavior.

▪ Interface Segregation Principle 

Clients shouldn’t be forced to depend on meth­ods they do not use.

▪ Try to make your inter­faces nar­row enough that client class­es don’t have to imple­ment behav­iors they don’t need.

▪ Accord­ing to the inter­face seg­re­ga­tion prin­ci­ple, you should break down “fat” inter­faces into more gran­u­lar and spe­cif­ic ones. Clients should imple­ment only those meth­ods that they real­ly need. Oth­er­wise, a change to a “fat” inter­face would break even clients that don’t use the changed methods.

▪ Class inher­i­tance lets a class have just one super­class, but it doesn’t limit the num­ber of inter­faces that the class can imple­ment at the same time. Hence, there’s no need to cram tons of unre­lat­ed meth­ods to a sin­gle inter­face. Break it down into sev­er­al more refined inter­faces—you can imple­ment them all in a sin­gle class if need­ed.

▪ At the time you assumed that all cloud providers have the same broad spec­trum of fea­tures as Ama­zon. But when it came to imple­ment­ing sup­port for anoth­er provider, it turned out that most of the inter­faces of the library are too wide. Some meth­ods describe fea­tures that other cloud providers just don’t have.

▪ While you can still imple­ment these meth­ods and put some stubs there, it wouldn’t be a pret­ty solu­tion. The bet­ter approach is to break down the inter­face into parts

▪ As with the other prin­ci­ples, you can go too far with this one. Don’t fur­ther divide an inter­face which is already quite spe­cif­ic. Remem­ber that the more inter­faces you cre­ate, the more com­plex your code becomes. Keep the balance.

▪ Dependency Inversion Principle 

High-level class­es shouldn’t depend on low-level class­es. Both should depend on abstrac­tions. Abstrac­tions shouldn’t depend on details. Details should depend on abstractions.

▪ Usu­al­ly when design­ing soft­ware, you can make a dis­tinc­tion between two lev­els of classes.

Low-level class­es imple­ment basic oper­a­tions such as work­ing with a disk, trans­fer­ring data over a net­work, con­nect­ing to a data­base, etc.
High-level class­es con­tain com­plex busi­ness logic that directs low-level class­es to do something.

▪ Some­times peo­ple design low-level class­es first and only then start work­ing on high-level ones. This is very com­mon when you start devel­op­ing a pro­to­type on a new sys­tem, and you’re not even sure what’s pos­si­ble at the high­er level because low-level stuff isn’t yet imple­ment­ed or clear. With such an approach busi­ness logic class­es tend to become depen­dent on prim­i­tive low-level classes.

▪ The depen­den­cy inver­sion prin­ci­ple sug­gests chang­ing the direc­tion of this dependency.

▪ For starters, you need to describe inter­faces for low-level oper­a­tions that high-level class­es rely on, prefer­ably in busi­ness terms.

▪ For instance, busi­ness logic should call a method openReport(file) rather than a series of meth­ods openFile(x), readBytes(n), closeFile(x). These inter­faces count as high-level ones.

▪ Now you can make high-level class­es depen­dent on those inter­faces, instead of on con­crete low-level class­es. This depen­den­cy will be much soft­er than the orig­i­nal one.

▪ Once low-level class­es imple­ment these inter­faces, they become depen­dent on the busi­ness logic level, revers­ing the direc­tion of the orig­i­nal dependency.

▪ The depen­den­cy inver­sion prin­ci­ple often goes along with the open/closed prin­ci­ple: you can extend low-level class­es to use with dif­fer­ent busi­ness logic class­es with­out break­ing exist­ing classes.

▪ In this exam­ple, the high-level bud­get report­ing class uses a low-level data­base class for read­ing and per­sist­ing its data. This means that any change in the low-level class, such as when a new ver­sion of the data­base serv­er gets released, may affect the high-level class, which isn’t sup­posed to care about the data stor­age details.

▪ You can fix this prob­lem by cre­at­ing a high-level inter­face that describes read/write oper­a­tions and mak­ing the report­ing class use that inter­face instead of the low-level class. Then you can change or extend the orig­i­nal low-level class to imple­ment the new read/write inter­face declared by the busi­ness logic.

▪ AFTER: low-level class­es depend on a high-level abstraction.

As a result, the direc­tion of the orig­i­nal depen­den­cy has been invert­ed: low-level class­es are now depen­dent on high-level abstractions.

▪ Fac­to­ry Method is a cre­ation­al design pat­tern that pro­vides an inter­face for cre­at­ing objects in a super­class, but allows sub­class­es to alter the type of objects that will be created.

▪ Imag­ine that you’re cre­at­ing a logis­tics man­age­ment appli­ca­tion. The first ver­sion of your app can only han­dle trans­porta­tion by trucks, so the bulk of your code lives inside the Truck class.

▪ Adding a new class to the pro­gram isn’t that sim­ple if the rest of the code is already cou­pled to exist­ing classes.

▪ At present, most of your code is cou­pled to the Truck class. Adding Ships into the app would require mak­ing changes to the entire code­base. More­over, if later you decide to add anoth­er type of trans­porta­tion to the app, you will prob­a­bly need to make all of these changes again.

▪ As a result, you will end up with pret­ty nasty code, rid­dled with con­di­tion­als that switch the app’s behav­ior depend­ing on the class of trans­porta­tion objects.

▪ The Fac­to­ry Method pat­tern sug­gests that you replace direct object con­struc­tion calls (using the new oper­a­tor) with calls to a spe­cial fac­to­ry method.

▪ Don’t worry: the objects are still cre­at­ed via the new oper­a­tor, but it’s being called from with­in the fac­to­ry method. Objects returned by a fac­to­ry method are often referred to as prod­ucts.

▪ All prod­ucts must fol­low the same interface.

▪ As long as all prod­uct class­es imple­ment a com­mon inter­face, you can pass their objects to the client code with­out break­ing it.

▪ The Prod­uct declares the inter­face, which is com­mon to all objects that can be pro­duced by the cre­ator and its subclasses.

▪ Con­crete Prod­ucts are dif­fer­ent imple­men­ta­tions of the prod­uct interface

▪ The Cre­ator class declares the fac­to­ry method that returns new prod­uct objects. It’s impor­tant that the return type of this method match­es the prod­uct interface.

▪ As an alter­na­tive, the base fac­to­ry method can return some default prod­uct type.

▪ Note, despite its name, prod­uct cre­ation is not the pri­ma­ry respon­si­bil­i­ty of the cre­ator. Usu­al­ly, the cre­ator class already has some core busi­ness logic relat­ed to prod­ucts. The fac­to­ry method helps to decou­ple this logic from the con­crete prod­uct class­es.

▪ Note that the fac­to­ry method doesn’t have to cre­ate new instances all the time. It can also return exist­ing objects from a cache, an object pool, or anoth­er source.

▪ The sub­class then inher­its most of the code from the base class, but, thanks to the fac­to­ry method, can ren­der Win­dows-look­ing but­tons on the screen.

▪ For this pat­tern to work, the base Dialog class must work with abstract but­tons: a base class or an inter­face that all con­crete but­tons fol­low. This way the code with­in Dialog remains func­tion­al, whichev­er type of but­tons it works with.

▪ Of course, you can apply this approach to other UI ele­ments as well. How­ev­er, with each new fac­to­ry method you add to the Dialog, you get clos­er to the Abstract Fac­to­ry pat­tern. Fear not, we’ll talk about this pat­tern later.

▪ Use the Fac­to­ry Method when you don’t know before­hand the exact types and depen­den­cies of the objects your code should work with

▪ The Fac­to­ry Method sep­a­rates prod­uct con­struc­tion code from the code that actu­al­ly uses the prod­uct. There­fore it’s eas­i­er to extend the prod­uct con­struc­tion code inde­pen­dent­ly from the rest of the code.

▪ Use the Fac­to­ry Method when you want to pro­vide users of your library or frame­work with a way to extend its inter­nal components.

▪ Use the Fac­to­ry Method when you want to save sys­tem resources by reusing exist­ing objects instead of rebuild­ing them each time.

▪ Prob­a­bly the most obvi­ous and con­ve­nient place where this code could be placed is the con­struc­tor of the class whose objects we’re try­ing to reuse. How­ev­er, a con­struc­tor must always return new objects by def­i­n­i­tion. It can’t return exist­ing instances.

There­fore, you need to have a reg­u­lar method capa­ble of cre­at­ing new objects as well as reusing exist­ing ones. That sounds very much like a fac­to­ry method.

▪ You avoid tight cou­pling between the cre­ator and the con­crete products.
Sin­gle Respon­si­bil­i­ty Prin­ci­ple. You can move the prod­uct cre­ation code into one place in the pro­gram, mak­ing the code eas­i­er to support.

▪ Open/Closed Prin­ci­ple. You can intro­duce new types of prod­ucts into the pro­gram with­out break­ing exist­ing client code.
The code may become more com­pli­cat­ed since you need to intro­duce a lot of new sub­class­es to imple­ment the pat­tern. The best case sce­nario is when you’re intro­duc­ing the pat­tern into an exist­ing hier­ar­chy of cre­ator classes.

▪ Many designs start by using Fac­to­ry Method (less com­pli­cat­ed and more cus­tomiz­able via sub­class­es) and evolve toward Abstract Fac­to­ry, Pro­to­type, or Builder (more flex­i­ble, but more complicated).

▪ Abstract Fac­to­ry class­es are often based on a set of Fac­to­ry Meth­ods, but you can also use Pro­to­type to com­pose the meth­ods on these classes

▪ You can use Fac­to­ry Method along with Iter­a­tor to let col­lec­tion sub­class­es return dif­fer­ent types of iter­a­tors that are com­pat­i­ble with the collections.

▪ Pro­to­type isn’t based on inher­i­tance, so it doesn’t have its draw­backs. On the other hand, Pro­to­type requires a com­pli­cat­ed ini­tial­iza­tion of the cloned object. Fac­to­ry Method is based on inher­i­tance but doesn’t require an ini­tial­iza­tion step.

▪ Fac­to­ry Method is a spe­cial­iza­tion of Tem­plate Method. At the same time, a Fac­to­ry Method may serve as a step in a large Tem­plate Method.

▪ Abstract Fac­to­ry is a cre­ation­al design pat­tern that lets you pro­duce fam­i­lies of relat­ed objects with­out spec­i­fy­ing their con­crete classes

▪ A fac­to­ry is a class that returns prod­ucts of a par­tic­u­lar kind. For exam­ple, the ModernFurnitureFactory can only cre­ate ModernChair, ModernSofa and ModernCoffeeTable objects.

▪ The client shouldn’t care about the con­crete class of the fac­to­ry it works with

▪ Abstract Prod­ucts declare inter­faces for a set of dis­tinct but relat­ed prod­ucts which make up a prod­uct family.

▪ Con­crete Prod­ucts are var­i­ous imple­men­ta­tions of abstract prod­ucts, grouped by vari­ants. Each abstract prod­uct (chair/sofa) must be imple­ment­ed in all given vari­ants (Vic­to­ri­an/Mod­ern).

▪ The Abstract Fac­to­ry inter­face declares a set of meth­ods for cre­at­ing each of the abstract products.

▪ Con­crete Fac­to­ries imple­ment cre­ation meth­ods of the abstract fac­to­ry. Each con­crete fac­to­ry cor­re­sponds to a spe­cif­ic vari­ant of prod­ucts and cre­ates only those prod­uct variants.

▪ It works like this: when an appli­ca­tion launch­es, it checks the type of the cur­rent oper­at­ing sys­tem. The app uses this infor­ma­tion to cre­ate a fac­to­ry object from a class that match­es the oper­at­ing sys­tem. The rest of the code uses this fac­to­ry to cre­ate UI ele­ments. This pre­vents the wrong ele­ments from being created.

▪ In a well-designed pro­gram each class is respon­si­ble only for one thing. When a class deals with mul­ti­ple prod­uct types, it may be worth extract­ing its fac­to­ry meth­ods into a stand-alone fac­to­ry class or a full-blown Abstract Fac­to­ry imple­men­ta­tion.

▪ Many designs start by using Fac­to­ry Method (less com­pli­cat­ed and more cus­tomiz­able via sub­class­es) and evolve toward Abstract Fac­to­ry, Pro­to­type, or Builder (more flex­i­ble, but more complicated).

▪ Builder focus­es on con­struct­ing com­plex objects step by step. Abstract Fac­to­ry spe­cial­izes in cre­at­ing fam­i­lies of relat­ed objects. Abstract Fac­to­ry returns the prod­uct imme­di­ate­ly, where­as Builder lets you run some addi­tion­al con­struc­tion steps before fetch­ing the product.

▪ Abstract Fac­to­ry class­es are often based on a set of Fac­to­ry Meth­ods, but you can also use Pro­to­type to com­pose the meth­ods on these classes

▪ Abstract Fac­to­ry can serve as an alter­na­tive to Facade when you only want to hide the way the sub­sys­tem objects are cre­at­ed from the client code.

▪ Abstract Fac­to­ries, Builders and Pro­to­types can all be imple­ment­ed as Sin­gle­tons.

▪ Builder is a cre­ation­al design pat­tern that lets you con­struct com­plex objects step by step

▪ Imag­ine a com­plex object that requires labo­ri­ous, step-by-step ini­tial­iza­tion of many fields and nest­ed objects. Such ini­tial­iza­tion code is usu­al­ly buried inside a mon­strous con­struc­tor with lots of para­me­ters. Or even worse: scat­tered all over the client code.

▪ There’s anoth­er approach that doesn’t involve breed­ing sub­class­es. You can cre­ate a giant con­struc­tor right in the base House class with all pos­si­ble para­me­ters that con­trol the house object. While this approach indeed elim­i­nates the need for sub­class­es, it cre­ates anoth­er problem.

▪ The con­struc­tor with lots of para­me­ters has its down­side: not all the para­me­ters are need­ed at all times.

In most cases most of the para­me­ters will be unused, mak­ing the con­struc­tor calls pret­ty ugly. For instance, only a frac­tion of hous­es have swim­ming pools, so the para­me­ters relat­ed to swim­ming pools will be use­less nine times out of ten.

▪ The Builder pat­tern sug­gests that you extract the object con­struc­tion code out of its own class and move it to sep­a­rate objects called builders.

▪ The Builder doesn’t allow other objects to access the prod­uct while it’s being built.

▪ The impor­tant part is that you don’t need to call all of the steps. You can call only those steps that are nec­es­sary for pro­duc­ing a par­tic­u­lar con­fig­u­ra­tion of an object.

▪ Some of the con­struc­tion steps might require dif­fer­ent imple­men­ta­tion when you need to build var­i­ous rep­re­sen­ta­tions of the prod­uct. For exam­ple, walls of a cabin may be built of wood, but the cas­tle walls must be built with stone.

In this case, you can cre­ate sev­er­al dif­fer­ent builder class­es that imple­ment the same set of build­ing steps, but in a dif­fer­ent man­ner. Then you can use these builders in the con­struc­tion process (i.e., an ordered set of calls to the build­ing steps) to pro­duce dif­fer­ent kinds of objects.

▪ Direc­tor

You can go fur­ther and extract a series of calls to the builder steps you use to con­struct a prod­uct into a sep­a­rate class called direc­tor

▪ How­ev­er, the direc­tor class might be a good place to put var­i­ous con­struc­tion rou­tines so you can reuse them across your program.

▪ The Builder inter­face declares prod­uct con­struc­tion steps that are com­mon to all types of builders.

▪ Con­crete Builders pro­vide dif­fer­ent imple­men­ta­tions of the con­struc­tion steps. Con­crete builders may pro­duce prod­ucts that don’t fol­low the com­mon interface.

▪ Prod­ucts are result­ing objects. Prod­ucts con­struct­ed by dif­fer­ent builders don’t have to belong to the same class hier­ar­chy or interface.

▪ This exam­ple of the Builder pat­tern illus­trates how you can reuse the same object con­struc­tion code when build­ing dif­fer­ent types of prod­ucts, such as cars, and cre­ate the cor­re­spond­ing man­u­als for them.

▪ A car is a com­plex object that can be con­struct­ed in a hun­dred dif­fer­ent ways. Instead of bloat­ing the Car class with a huge con­struc­tor, we extract­ed the car assem­bly code into a sep­a­rate car builder class

▪ If the client code needs to assem­ble a spe­cial, fine-tuned model of a car, it can work with the builder direct­ly. On the other hand, the client can del­e­gate the assem­bly to the direc­tor class, which knows how to use a builder to con­struct sev­er­al of the most pop­u­lar mod­els of cars.

▪ The man­u­al describes every fea­ture of the car, so the details in the man­u­als vary across the dif­fer­ent mod­els. That’s why it makes sense to reuse an exist­ing con­struc­tion process for both real cars and their respec­tive man­u­als. Of course, build­ing a man­u­al isn’t the same as build­ing a car, and that’s why we must pro­vide anoth­er builder class that spe­cial­izes in com­pos­ing man­u­als.

▪  Usually, after returning the end result to the client, a
  // builder instance is expected to be ready to start
  // producing another product. That's why it's a usual
  // practice to call the reset method at the end of the
  // `getProduct` method body. However, this behavior isn't
  // mandatory, and you can make your builder wait for an
  // explicit reset call from the client code before disposing
  // of the previous result.

▪  The final product is often retrieved from a builder
    // object since the director isn't aware of and not
    // dependent on concrete builders and products.
    Manual manual = builder.getProduct()

▪ Use the Builder pat­tern to get rid of a “tele­scop­ing constructor”.

Say you have a con­struc­tor with ten option­al para­me­ters. Call­ing such a beast is very incon­ve­nient; there­fore, you over­load the con­struc­tor and cre­ate sev­er­al short­er ver­sions with fewer para­me­ters. These con­struc­tors still refer to the main one, pass­ing some default val­ues into any omit­ted parameters.

class Pizza {
  Pizza(int size) { ... }
  Pizza(int size, boolean cheese) { ... }
  Pizza(int size, boolean cheese, boolean pepperoni) { ... }
  // ...

Cre­at­ing such a mon­ster is only pos­si­ble in lan­guages that sup­port method over­load­ing, such as C# or Java

▪ The Builder pat­tern lets you con­struct prod­ucts step-by-step. You could defer exe­cu­tion of some steps with­out break­ing the final prod­uct

▪ You can even call steps recur­sive­ly, which comes in handy when you need to build an object tree.

▪ A builder doesn’t expose the unfin­ished prod­uct while run­ning con­struc­tion steps. This pre­vents the client code from fetch­ing an incom­plete result.

▪ You can con­struct objects step-by-step, defer con­struc­tion steps or run steps recursively.
You can reuse the same con­struc­tion code when build­ing var­i­ous rep­re­sen­ta­tions of products.
Sin­gle Respon­si­bil­i­ty Prin­ci­ple. You can iso­late com­plex con­struc­tion code from the busi­ness logic of the product.
The over­all com­plex­i­ty of the code increas­es since the pat­tern requires cre­at­ing mul­ti­ple new classes.

▪ Pro­to­type is a cre­ation­al design pat­tern that lets you copy exist­ing objects with­out mak­ing your code depen­dent on their classes.

▪ The Pro­to­type pat­tern del­e­gates the cloning process to the actu­al objects that are being cloned. The pat­tern declares a com­mon inter­face for all objects that sup­port cloning. This inter­face lets you clone an object with­out cou­pling your code to the class of that object. Usu­al­ly, such an inter­face con­tains just a sin­gle clone method.

▪ An object that sup­ports cloning is called a pro­to­type.

▪ Pre-built pro­to­types can be an alter­na­tive to subclassing.

▪ Here’s how it works: you cre­ate a set of objects, con­fig­ured in var­i­ous ways. When you need an object like the one you’ve con­fig­ured, you just clone a pro­to­type instead of con­struct­ing a new object from scratch.

▪ The Pro­to­type inter­face declares the cloning meth­ods. In most cases, it’s a sin­gle clone method.

▪ The Pro­to­type Reg­istry pro­vides an easy way to access fre­quent­ly-used pro­to­types. It stores a set of pre-built objects that are ready to be copied. The sim­plest pro­to­type reg­istry is a name → prototype
hash map.

▪  Performing all the actual copying in the constructor helps to
// keep the result consistent: the constructor will not return a
// result until the new object is fully built; thus, no object
// can have a reference to a partially-built clone.
class Rectangle extends Shape is
  field width: int
  field height: int

▪ This hap­pens a lot when your code works with objects passed to you from 3rd-party code via some inter­face. The con­crete class­es of these objects are unknown, and you couldn’t depend on them even if you want­ed to.

▪ The Pro­to­type pat­tern pro­vides the client code with a gen­er­al inter­face for work­ing with all objects that sup­port cloning. This inter­face makes the client code inde­pen­dent from the con­crete class­es of objects that it clones.

▪ Cre­ate the pro­to­type inter­face and declare the clone method in it. Or just add the method to all class­es of an exist­ing class hier­ar­chy, if you have one.

▪ You can clone objects with­out cou­pling to their con­crete classes.
You can get rid of repeat­ed ini­tial­iza­tion code in favor of cloning pre-built prototypes.

▪ Pro­to­type isn’t based on inher­i­tance, so it doesn’t have its draw­backs. On the other hand, Pro­to­type requires a com­pli­cat­ed ini­tial­iza­tion of the cloned object.

▪ Ensure that a class has just a sin­gle instance. Why would any­one want to con­trol how many instances a class has? The most com­mon rea­son for this is to con­trol access to some shared resource—for exam­ple, a data­base or a file.

▪ Clients may not even real­ize that they’re work­ing with the same object all the time.

▪ Just like a glob­al vari­able, the Sin­gle­ton pat­tern lets you access some object from any­where in the pro­gram. How­ev­er, it also pro­tects that instance from being over­writ­ten by other code.

▪ Nowa­days, the Sin­gle­ton pat­tern has become so pop­u­lar that peo­ple may call some­thing a sin­gle­ton even if it solves just one of the list­ed problems.

▪ All imple­men­ta­tions of the Sin­gle­ton have these two steps in common:

▪ Make the default con­struc­tor pri­vate, to pre­vent other objects from using the new oper­a­tor with the Sin­gle­ton class

▪ Cre­ate a sta­t­ic cre­ation method that acts as a con­struc­tor. Under the hood, this method calls the pri­vate con­struc­tor to cre­ate an object and saves it in a sta­t­ic field. All fol­low­ing calls to this method return the cached object.

▪ In this exam­ple, the data­base con­nec­tion class acts as a Sin­gle­ton. This class doesn’t have a pub­lic con­struc­tor, so the only way to get its object is to call the getInstance method. This method caches the first cre­at­ed object and returns it in all sub­se­quent calls.

▪  The static method that controls access to the singleton
  // instance.
  public static method getInstance() is
    if (Database.instance == null) then

▪ acquireThreadLock() and then
        // Ensure that the instance hasn't yet been
        // initialized by another thread while this one
        // has been waiting for the lock's release.

▪ Use the Sin­gle­ton pat­tern when a class in your pro­gram should have just a sin­gle instance avail­able to all clients

▪ The Sin­gle­ton pat­tern can mask bad design, for instance, when the com­po­nents of the pro­gram know too much about each other.

▪ The pat­tern requires spe­cial treat­ment in a mul­ti­thread­ed envi­ron­ment so that mul­ti­ple threads won’t cre­ate a sin­gle­ton object sev­er­al times.

▪ A Facade class can often be trans­formed into a Sin­gle­ton since a sin­gle facade object is suf­fi­cient in most cases

▪ Fly­weight would resem­ble Sin­gle­ton if you some­how man­aged to reduce all shared states of the objects to just one fly­weight object

▪ There should be only one Sin­gle­ton instance, where­as a Fly­weight class can have mul­ti­ple instances with dif­fer­ent intrin­sic states.

▪ The Sin­gle­ton object can be muta­ble. Fly­weight objects are immutable.

▪ Struc­tur­al design pat­terns explain how to assem­ble objects and class­es into larg­er struc­tures, while keep­ing these struc­tures flex­i­ble and efficient.

▪ Adapter is a struc­tur­al design pat­tern that allows objects with incom­pat­i­ble inter­faces to collaborate

▪ You can cre­ate an adapter. This is a spe­cial object that con­verts the inter­face of one object so that anoth­er object can under­stand it.

▪ The adapter gets an inter­face, com­pat­i­ble with one of the exist­ing objects

▪ Using this inter­face, the exist­ing object can safe­ly call the adapter’s methods.

▪ Upon receiv­ing a call, the adapter pass­es the request to the sec­ond object, but in a for­mat and order that the sec­ond object expects.

▪ Some­times it’s even pos­si­ble to cre­ate a two-way adapter that can con­vert the calls in both directions.

▪ When you trav­el from the US to Europe for the first time, you may get a sur­prise when try­ing to charge your lap­top. The power plug and sock­ets stan­dards are dif­fer­ent in dif­fer­ent coun­tries. That’s why your US plug won’t fit a Ger­man sock­et. The prob­lem can be solved by using a power plug adapter that has the Amer­i­can-style sock­et and the Euro­pean-style plug.

▪ This imple­men­ta­tion uses the object com­po­si­tion prin­ci­ple: the adapter imple­ments the inter­face of one object and wraps the other one.

▪ The Adapter pat­tern lets you cre­ate a mid­dle-layer class that serves as a trans­la­tor between your code and a lega­cy class, a 3rd-party class or any other class with a weird interface.

▪ A use­ful ser­vice class, which you can’t change (often 3rd-party, lega­cy or with lots of exist­ing dependencies).

▪ Bridge is usu­al­ly designed up-front, let­ting you devel­op parts of an appli­ca­tion inde­pen­dent­ly of each other. On the other hand, Adapter is com­mon­ly used with an exist­ing app to make some oth­er­wise-incom­pat­i­ble class­es work togeth­er nicely.

▪ With Adapter you access an exist­ing object via dif­fer­ent inter­face. With Proxy, the inter­face stays the same. With Dec­o­ra­tor you access the object via an enhanced interface.

▪ Facade defines a new inter­face for exist­ing objects, where­as Adapter tries to make the exist­ing inter­face usable. Adapter usu­al­ly wraps just one object, while Facade works with an entire sub­sys­tem of objects.

▪ Bridge, State, Strat­e­gy (and to some degree Adapter) have very sim­i­lar struc­tures. Indeed, all of these pat­terns are based on com­po­si­tion, which is del­e­gat­ing work to other objects.

▪ A pat­tern isn’t just a recipe for struc­tur­ing your code in a spe­cif­ic way. It can also com­mu­ni­cate to other devel­op­ers the prob­lem the pat­tern solves.

▪ Bridge is a struc­tur­al design pat­tern that lets you split a large class or a set of close­ly relat­ed class­es into two sep­a­rate hier­ar­chies—abstrac­tion and imple­men­ta­tion—which can be devel­oped inde­pen­dent­ly of each other.

▪ Say you have a geo­met­ric Shape class with a pair of sub­class­es: Circle and Square. You want to extend this class hier­ar­chy to incor­po­rate col­ors, so you plan to cre­ate Red and Blue shape sub­class­es. How­ev­er, since you already have two sub­class­es, you’ll need to cre­ate four class com­bi­na­tions such as BlueCircle and RedSquare.

▪ Num­ber of class com­bi­na­tions grows in geo­met­ric progression.

▪ The Bridge pat­tern attempts to solve this prob­lem by switch­ing from inher­i­tance to the object com­po­si­tion.

▪ Fol­low­ing this approach, we can extract the color-relat­ed code into its own class with two sub­class­es: Red and Blue. The Shape class then gets a ref­er­ence field point­ing to one of the color objects. Now the shape can del­e­gate any color-relat­ed work to the linked color object. That ref­er­ence will act as a bridge between the Shape and Color class­es.

▪ Abstrac­tion (also called inter­face) is a high-level con­trol layer for some enti­ty. This layer isn’t sup­posed to do any real work on its own. It should del­e­gate the work to the imple­men­ta­tion layer (also called plat­form).

▪ Mak­ing even a sim­ple change to a mono­lith­ic code­base is pret­ty hard because you must under­stand the entire thing very well. Mak­ing changes to small­er, well-defined mod­ules is much easier.

▪ Let’s try to solve this issue with the Bridge pat­tern. It sug­gests that we divide the class­es into two hierarchies:

Abstrac­tion: the GUI layer of the app.
Imple­men­ta­tion: the oper­at­ing sys­tems’ APIs.

▪ The Abstrac­tion pro­vides high-level con­trol logic. It relies on the imple­men­ta­tion object to do the actu­al low-level work.

▪ The Imple­men­ta­tion declares the inter­face that’s com­mon for all con­crete imple­men­ta­tions. An abstrac­tion can only com­mu­ni­cate with an imple­men­ta­tion object via meth­ods that are declared here.

▪ Con­crete Imple­men­ta­tions con­tain plat­form-spe­cif­ic code

▪ Refined Abstrac­tions pro­vide vari­ants of con­trol logic. Like their par­ent, they work with dif­fer­ent imple­men­ta­tions via the gen­er­al imple­men­ta­tion interface.

▪ This exam­ple illus­trates how the Bridge pat­tern can help divide the mono­lith­ic code of an app that man­ages devices and their remote con­trols. The Device class­es act as the imple­men­ta­tion, where­as the Remotes act as the abstraction.

▪ Use the Bridge pat­tern when you want to divide and orga­nize a mono­lith­ic class that has sev­er­al vari­ants of some func­tion­al­i­ty (for exam­ple, if the class can work with var­i­ous data­base servers).

▪ The big­ger a class becomes, the hard­er it is to fig­ure out how it works, and the longer it takes to make a change. The changes made to one of the vari­a­tions of func­tion­al­i­ty may require mak­ing changes across the whole class, which often results in mak­ing errors or not address­ing some crit­i­cal side effects.

▪ Use the pat­tern when you need to extend a class in sev­er­al orthog­o­nal (inde­pen­dent) dimensions.

▪ The Bridge sug­gests that you extract a sep­a­rate class hier­ar­chy for each of the dimen­sions. The orig­i­nal class del­e­gates the relat­ed work to the objects belong­ing to those hier­ar­chies instead of doing every­thing on its own.

▪ Although it’s option­al, the Bridge pat­tern lets you replace the imple­men­ta­tion object inside the abstrac­tion. It’s as easy as assign­ing a new value to a field.

By the way, this last item is the main rea­son why so many peo­ple con­fuse the Bridge with the Strat­e­gy pat­tern.

▪ Remem­ber that a pat­tern is more than just a cer­tain way to struc­ture your class­es. It may also com­mu­ni­cate intent and a prob­lem being addressed.

▪ Iden­ti­fy the orthog­o­nal dimen­sions in your class­es. These inde­pen­dent con­cepts could be: abstrac­tion/plat­form, domain/infra­struc­ture, front-end/back-end, or inter­face/imple­men­ta­tion.

▪ See what oper­a­tions the client needs and define them in the base abstrac­tion class.

▪ Bridge is usu­al­ly designed up-front, let­ting you devel­op parts of an appli­ca­tion inde­pen­dent­ly of each other. On the other hand, Adapter is com­mon­ly used with an exist­ing app to make some oth­er­wise-incom­pat­i­ble class­es work togeth­er nicely.

▪ Bridge, State, Strat­e­gy (and to some degree Adapter) have very sim­i­lar struc­tures. Indeed, all of these pat­terns are based on com­po­si­tion, which is del­e­gat­ing work to other objects. How­ev­er, they all solve dif­fer­ent prob­lems

▪ A pat­tern isn’t just a recipe for struc­tur­ing your code in a spe­cif­ic way. It can also com­mu­ni­cate to other devel­op­ers the prob­lem the pat­tern solves.

▪ You can use Abstract Fac­to­ry along with Bridge. This pair­ing is use­ful when some abstrac­tions defined by Bridge can only work with spe­cif­ic imple­men­ta­tions. In this case, Abstract Fac­to­ry can encap­su­late these rela­tions and hide the com­plex­i­ty from the client code.

▪ Composite 

Also known as: Object Tree

Com­pos­ite is a struc­tur­al design pat­tern that lets you com­pose objects into tree struc­tures and then work with these struc­tures as if they were indi­vid­ual objects.

▪ For exam­ple, imag­ine that you have two types of objects: Products and Boxes. A Box can con­tain sev­er­al Products as well as a num­ber of small­er Boxes. These lit­tle Boxes can also hold some Products or even small­er Boxes, and so on.

▪ An order might com­prise var­i­ous prod­ucts, pack­aged in boxes, which are pack­aged in big­ger boxes and so on. The whole struc­ture looks like an upside down tree.

▪ The Com­pos­ite pat­tern sug­gests that you work with Products and Boxes through a com­mon inter­face which declares a method for cal­cu­lat­ing the total price.

▪ The Com­pos­ite pat­tern lets you run a behav­ior recur­sive­ly over all com­po­nents of an object tree.

▪ The Com­po­nent inter­face describes oper­a­tions that are com­mon to both sim­ple and com­plex ele­ments of the tree.

▪ The Leaf is a basic ele­ment of a tree that doesn’t have sub-ele­ments.

Usu­al­ly, leaf com­po­nents end up doing most of the real work, since they don’t have any­one to del­e­gate the work to.

▪ The Con­tain­er (aka com­pos­ite) is an ele­ment that has sub-ele­ments: leaves or other con­tain­ers. A con­tain­er doesn’t know the con­crete class­es of its chil­dren. It works with all sub-ele­ments only via the com­po­nent interface.

▪ Upon receiv­ing a request, a con­tain­er del­e­gates the work to its sub-ele­ments, process­es inter­me­di­ate results and then returns the final result to the client.

▪ The Client works with all ele­ments through the com­po­nent inter­face. As a result, the client can work in the same way with both sim­ple or com­plex ele­ments of the tree.

▪ The CompoundGraphic class is a con­tain­er that can com­prise any num­ber of sub-shapes, includ­ing other com­pound shapes. A com­pound shape has the same meth­ods as a sim­ple shape. How­ev­er, instead of doing some­thing on its own, a com­pound shape pass­es the request recur­sive­ly to all its chil­dren and “sums up” the result.

▪ The client code works with all shapes through the sin­gle inter­face com­mon to all shape class­es. Thus, the client doesn’t know whether it’s work­ing with a sim­ple shape or a com­pound one

▪ The client can work with very com­plex object struc­tures with­out being cou­pled to con­crete class­es that form that structure.

▪  The client code works with all the components via their base
// interface. This way the client code can support simple leaf
// components as well as complex composites.

▪ Use the Com­pos­ite pat­tern when you have to imple­ment a tree-like object structure.

▪ You can work with com­plex tree struc­tures more con­ve­nient­ly: use poly­mor­phism and recur­sion to your advantage.

▪ It might be dif­fi­cult to pro­vide a com­mon inter­face for class­es whose func­tion­al­i­ty dif­fers too much. In cer­tain sce­nar­ios, you’d need to over­gen­er­al­ize the com­po­nent inter­face, mak­ing it hard­er to comprehend.

▪ You can use Builder when cre­at­ing com­plex Com­pos­ite trees because you can pro­gram its con­struc­tion steps to work recursively.

▪ You can use Iter­a­tors to tra­verse Com­pos­ite trees.

▪ You can use Vis­i­tor to exe­cute an oper­a­tion over an entire Com­pos­ite tree.

▪ You can imple­ment shared leaf nodes of the Com­pos­ite tree as Fly­weights to save some RAM.

▪ Designs that make heavy use of Com­pos­ite and Dec­o­ra­tor can often ben­e­fit from using Pro­to­type. Apply­ing the pat­tern lets you clone com­plex struc­tures instead of re-con­struct­ing them from scratch.

▪ Dec­o­ra­tor is a struc­tur­al design pat­tern that lets you attach new behav­iors to objects by plac­ing these objects inside spe­cial wrap­per objects that con­tain the behaviors.

▪ At some point, you real­ize that users of the library expect more than just email noti­fi­ca­tions. Many of them would like to receive an SMS about crit­i­cal issues. Oth­ers would like to be noti­fied on Face­book and, of course, the cor­po­rate users would love to get Slack noti­fi­ca­tions.

▪ Each noti­fi­ca­tion type is imple­ment­ed as a noti­fi­er’s subclass.

▪ Com­bi­na­to­r­i­al explo­sion of subclasses.

▪ How­ev­er, inher­i­tance has sev­er­al seri­ous caveats that you need to be aware of.

▪ Inher­i­tance is sta­t­ic. You can’t alter the behav­ior of an exist­ing object at run­time. You can only replace the whole object with anoth­er one that’s cre­at­ed from a dif­fer­ent subclass.

▪ Sub­class­es can have just one par­ent class. In most lan­guages, inher­i­tance doesn’t let a class inher­it behav­iors of mul­ti­ple class­es at the same time.

▪ One of the ways to over­come these caveats is by using Aggre­ga­tion or Com­po­si­tion 9 instead of Inher­i­tance. Both of the alter­na­tives work almost the same way: one object has a ref­er­ence to anoth­er and del­e­gates it some work, where­as with inher­i­tance, the object itself is able to do that work, inher­it­ing the behav­ior from its superclass.

▪ “Wrap­per” is the alter­na­tive nick­name for the Dec­o­ra­tor pat­tern that clear­ly express­es the main idea of the pat­tern. A wrap­per is an object that can be linked with some tar­get object. The wrap­per con­tains the same set of meth­ods as the tar­get and del­e­gates to it all requests it receives. How­ev­er, the wrap­per may alter the result by doing some­thing either before or after it pass­es the request to the target.

▪ Wear­ing clothes is an exam­ple of using dec­o­ra­tors. When you’re cold, you wrap your­self in a sweater. If you’re still cold with a sweater, you can wear a jack­et on top. If it’s rain­ing, you can put on a rain­coat. All of these gar­ments “extend” your basic behav­ior but aren’t part of you, and you can eas­i­ly take off any piece of cloth­ing when­ev­er you don’t need it.

▪ The Com­po­nent declares the com­mon inter­face for both wrap­pers and wrapped objects.

▪ The Client can wrap com­po­nents in mul­ti­ple lay­ers of dec­o­ra­tors, as long as it works with all objects via the com­po­nent interface.

▪ Use the Dec­o­ra­tor pat­tern when you need to be able to assign extra behav­iors to objects at run­time with­out break­ing the code that uses these objects.

▪ The Dec­o­ra­tor lets you struc­ture your busi­ness logic into lay­ers, cre­ate a dec­o­ra­tor for each layer and com­pose objects with var­i­ous com­bi­na­tions of this logic at run­time. The client code can treat all these objects in the same way, since they all fol­low a com­mon interface.

▪ You can extend an object’s behav­ior with­out mak­ing a new subclass.

▪ Adapter pro­vides a com­plete­ly dif­fer­ent inter­face for access­ing an exist­ing object. On the other hand, with the Dec­o­ra­tor pat­tern the inter­face either stays the same or gets extend­ed. In addi­tion, Dec­o­ra­tor sup­ports recur­sive com­po­si­tion, which isn’t pos­si­ble when you use Adapter.

▪ With Adapter you access an exist­ing object via dif­fer­ent inter­face. With Proxy, the inter­face stays the same. With Dec­o­ra­tor you access the object via an enhanced interface.

▪ Chain of Respon­si­bil­i­ty and Dec­o­ra­tor have very sim­i­lar class struc­tures. Both pat­terns rely on recur­sive com­po­si­tion to pass the exe­cu­tion through a series of objects. How­ev­er, there are sev­er­al cru­cial differences

▪ The CoR han­dlers can exe­cute arbi­trary oper­a­tions inde­pen­dent­ly of each other. They can also stop pass­ing the request fur­ther at any point. On the other hand, var­i­ous Dec­o­ra­tors can extend the object’s behav­ior while keep­ing it con­sis­tent with the base inter­face. In addi­tion, dec­o­ra­tors aren’t allowed to break the flow of the request.

▪ A Dec­o­ra­tor is like a Com­pos­ite but only has one child com­po­nent. There’s anoth­er sig­nif­i­cant dif­fer­ence: Dec­o­ra­tor adds addi­tion­al respon­si­bil­i­ties to the wrapped object, while Com­pos­ite just “sums up” its chil­dren’s results.

▪ Dec­o­ra­tor lets you change the skin of an object, while Strat­e­gy lets you change the guts.

▪ Dec­o­ra­tor and Proxy have sim­i­lar struc­tures, but very dif­fer­ent intents. Both pat­terns are built on the com­po­si­tion prin­ci­ple, where one object is sup­posed to del­e­gate some of the work to anoth­er. The dif­fer­ence is that a Proxy usu­al­ly man­ages the life cycle of its ser­vice object on its own, where­as the com­po­si­tion of Dec­o­ra­tors is always con­trolled by the client.

▪ A facade is a class that pro­vides a sim­ple inter­face to a com­plex sub­sys­tem which con­tains lots of mov­ing parts. A facade might pro­vide lim­it­ed func­tion­al­i­ty in com­par­i­son to work­ing with the sub­sys­tem direct­ly. How­ev­er, it includes only those fea­tures that clients real­ly care about.

▪ Hav­ing a facade is handy when you need to inte­grate your app with a sophis­ti­cat­ed library that has dozens of fea­tures, but you just need a tiny bit of its func­tion­al­i­ty.

▪ For instance, an app that uploads short funny videos with cats to social media could poten­tial­ly use a pro­fes­sion­al video con­ver­sion library. How­ev­er, all that it real­ly needs is a class with the sin­gle method encode(filename, format)
. After cre­at­ing such a class and con­nect­ing it with the video con­ver­sion library, you’ll have your first facade.

▪ The Facade pro­vides con­ve­nient access to a par­tic­u­lar part of the sub­sys­tem’s func­tion­al­i­ty. It knows where to direct the client’s request and how to oper­ate all the mov­ing parts.

▪ Sub­sys­tem class­es aren’t aware of the facade’s exis­tence. They oper­ate with­in the sys­tem and work with each other directly.

▪ An exam­ple of iso­lat­ing mul­ti­ple depen­den­cies with­in a sin­gle facade class.

▪ Often, sub­sys­tems get more com­plex over time. Even apply­ing design pat­terns typ­i­cal­ly leads to cre­at­ing more class­es. A sub­sys­tem may become more flex­i­ble and eas­i­er to reuse in var­i­ous con­texts, but the amount of con­fig­u­ra­tion and boil­er­plate code it demands from a client grows ever larg­er. The Facade attempts to fix this prob­lem by pro­vid­ing a short­cut to the most-used fea­tures of the sub­sys­tem which fit most client requirements.

▪ Use the Facade when you want to struc­ture a sub­sys­tem into layers.

Cre­ate facades to define entry points to each level of a sub­sys­tem. You can reduce cou­pling between mul­ti­ple sub­sys­tems by requir­ing them to com­mu­ni­cate only through facades.

▪ To get the full ben­e­fit from the pat­tern, make all the client code com­mu­ni­cate with the sub­sys­tem only via the facade. Now the client code is pro­tect­ed from any changes in the sub­sys­tem code.

▪ Facade defines a new inter­face for exist­ing objects, where­as Adapter tries to make the exist­ing inter­face usable. Adapter usu­al­ly wraps just one object, while Facade works with an entire sub­sys­tem of objects.

▪ Abstract Fac­to­ry can serve as an alter­na­tive to Facade when you only want to hide the way the sub­sys­tem objects are cre­at­ed from the client code.

▪ Facade and Medi­a­tor have sim­i­lar jobs: they try to orga­nize col­lab­o­ra­tion between lots of tight­ly cou­pled classes.

▪ Facade defines a sim­pli­fied inter­face to a sub­sys­tem of objects, but it doesn’t intro­duce any new func­tion­al­i­ty.

▪ The sub­sys­tem itself is unaware of the facade.

▪ Objects with­in the sub­sys­tem can com­mu­ni­cate directly.

▪ Medi­a­tor cen­tral­izes com­mu­ni­ca­tion between com­po­nents of the sys­tem. The com­po­nents only know about the medi­a­tor object and don’t com­mu­ni­cate directly.

▪ A Facade class can often be trans­formed into a Sin­gle­ton since a sin­gle facade object is suf­fi­cient in most cases.

▪ Facade is sim­i­lar to Proxy in that both buffer a com­plex enti­ty and ini­tial­ize it on its own. Unlike Facade, Proxy has the same inter­face as its ser­vice object, which makes them inter­change­able.

▪ Fly­weight is a struc­tur­al design pat­tern that lets you fit more objects into the avail­able amount of RAM by shar­ing com­mon parts of state between mul­ti­ple objects instead of keep­ing all of the data in each object.

▪ On clos­er inspec­tion of the Particle class, you may notice that the color and sprite fields con­sume a lot more mem­o­ry than other fields. What’s worse is that these two fields store almost iden­ti­cal data across all par­ti­cles. For exam­ple, all bul­lets have the same color and sprite.

▪ As you’ve prob­a­bly guessed by now, an object that only stores the intrin­sic state is called a fly­weight.

▪ Where does the extrin­sic state move to? Some class should still store it, right? In most cases, it gets moved to the con­tain­er object, which aggre­gates objects before we apply the pattern.

In our case, that’s the main Game object that stores all par­ti­cles in the particles field.

▪ Since the same fly­weight object can be used in dif­fer­ent con­texts, you have to make sure that its state can’t be mod­i­fied. A fly­weight should ini­tial­ize its state just once, via con­struc­tor para­me­ters. It shouldn’t expose any set­ters or pub­lic fields to other objects.

▪ For more con­ve­nient access to var­i­ous fly­weights, you can cre­ate a fac­to­ry method that man­ages a pool of exist­ing fly­weight objects. The method accepts the intrin­sic state of the desired fly­weight from a client, looks for an exist­ing fly­weight object match­ing this state, and returns it if it was found. If not, it cre­ates a new fly­weight and adds it to the pool.

▪ The Fly­weight pat­tern is mere­ly an opti­miza­tion. Before apply­ing it, make sure your pro­gram does have the RAM con­sump­tion prob­lem relat­ed to hav­ing a mas­sive num­ber of sim­i­lar objects in mem­o­ry at the same time. Make sure that this prob­lem can’t be solved in any other mean­ing­ful way

▪ The Fly­weight class con­tains the por­tion of the orig­i­nal object’s state that can be shared between mul­ti­ple objects. The same fly­weight object can be used in many dif­fer­ent con­texts. The state stored inside a fly­weight is called intrin­sic. The state passed to the fly­weight’s meth­ods is called extrin­sic.

▪ The Con­text class con­tains the extrin­sic state, unique across all orig­i­nal objects. When a con­text is paired with one of the fly­weight objects, it rep­re­sents the full state of the orig­i­nal object.

▪ In this exam­ple, the Fly­weight pat­tern helps to reduce mem­o­ry usage when ren­der­ing mil­lions of tree objects on a canvas

▪ Use the Fly­weight pat­tern only when your pro­gram must sup­port a huge num­ber of objects which bare­ly fit into avail­able RAM.

▪ Option­al­ly, cre­ate a fac­to­ry class to man­age the pool of fly­weights. It should check for an exist­ing fly­weight before cre­at­ing a new one. Once the fac­to­ry is in place, clients must only request fly­weights through it. They should describe the desired fly­weight by pass­ing its intrin­sic state to the factory.

▪ You can save lots of RAM, assum­ing your pro­gram has tons of sim­i­lar objects.
You might be trad­ing RAM over CPU cycles when some of the con­text data needs to be recal­cu­lat­ed each time some­body calls a fly­weight method.
The code becomes much more com­pli­cat­ed. New team mem­bers will always be won­der­ing why the state of an enti­ty was sep­a­rat­ed in such a way.

▪ Fly­weight objects are immutable.

▪ Proxy is a struc­tur­al design pat­tern that lets you pro­vide a sub­sti­tute or place­hold­er for anoth­er object

▪ A proxy con­trols access to the orig­i­nal object, allow­ing you to per­form some­thing either before or after the request gets through to the orig­i­nal object.

▪ You could imple­ment lazy ini­tial­iza­tion: cre­ate this object only when it’s actu­al­ly need­ed. All of the object’s clients would need to exe­cute some deferred ini­tial­iza­tion code.

▪ The proxy dis­guis­es itself as a data­base object. It can han­dle lazy ini­tial­iza­tion and result caching with­out the client or the real data­base object even knowing.

▪ Since the proxy imple­ments the same inter­face as the orig­i­nal class, it can be passed to any client that expects a real ser­vice object.

▪ The Ser­vice Inter­face declares the inter­face of the Ser­vice. The proxy must fol­low this inter­face to be able to dis­guise itself as a ser­vice object.

▪ The Client should work with both ser­vices and prox­ies via the same inter­face. This way you can pass a proxy into any code that expects a ser­vice object.

▪ The library pro­vides us with the video down­load­ing class. How­ev­er, it’s very inef­fi­cient. If the client appli­ca­tion requests the same video mul­ti­ple times, the library just down­loads it over and over, instead of caching and reusing the first down­loaded file.

The proxy class imple­ments the same inter­face as the orig­i­nal down­loader and del­e­gates it all the work. How­ev­er, it keeps track of the down­loaded files and returns the cached result when the app requests the same video mul­ti­ple times.

▪ Lazy ini­tial­iza­tion (vir­tu­al proxy). This is when you have a heavy­weight ser­vice object that wastes sys­tem resources by being always up, even though you only need it from time to time.

Instead of cre­at­ing the object when the app launch­es, you can delay the object’s ini­tial­iza­tion to a time when it’s real­ly needed.

▪ Access con­trol (pro­tec­tion proxy). This is when you want only spe­cif­ic clients to be able to use the ser­vice object; for instance, when your objects are cru­cial parts of an oper­at­ing sys­tem and clients are var­i­ous launched appli­ca­tions (includ­ing mali­cious ones).

The proxy can pass the request to the ser­vice object only if the client’s cre­den­tials match some criteria.

▪ Local exe­cu­tion of a remote ser­vice (remote proxy). This is when the ser­vice object is locat­ed on a remote server.

In this case, the proxy pass­es the client request over the net­work, han­dling all of the nasty details of work­ing with the network.

▪ Log­ging requests (log­ging proxy). This is when you want to keep a his­to­ry of requests to the ser­vice object.

The proxy can log each request before pass­ing it to the service.

▪ Caching request results (caching proxy). This is when you need to cache results of client requests and man­age the life cycle of this cache, espe­cial­ly if results are quite large.

The proxy can imple­ment caching for recur­ring requests that always yield the same results. The proxy may use the para­me­ters of requests as the cache keys.

▪ Smart ref­er­ence. This is when you need to be able to dis­miss a heavy­weight object once there are no clients that use it.

The proxy can keep track of clients that obtained a ref­er­ence to the ser­vice object or its results. From time to time, the proxy may go over the clients and check whether they are still active. If the client list gets empty, the proxy might dis­miss the ser­vice object and free the under­ly­ing sys­tem resources.

The proxy can also track whether the client had mod­i­fied the ser­vice object. Then the unchanged objects may be reused by other clients.

▪ If there’s no pre-exist­ing ser­vice inter­face, cre­ate one to make proxy and ser­vice objects inter­change­able. Extract­ing the inter­face from the ser­vice class isn’t always pos­si­ble, because you’d need to change all of the ser­vice’s clients to use that inter­face. Plan B is to make the proxy a sub­class of the ser­vice class, and this way it’ll inher­it the inter­face of the service.

▪ Cre­ate the proxy class. It should have a field for stor­ing a ref­er­ence to the ser­vice. Usu­al­ly, prox­ies cre­ate and man­age the whole life cycle of their ser­vices. On rare occa­sions, a ser­vice is passed to the proxy via a con­struc­tor by the client.

▪ With Adapter you access an exist­ing object via dif­fer­ent inter­face. With Proxy, the inter­face stays the same. With Dec­o­ra­tor you access the object via an enhanced interface.

▪ Facade is sim­i­lar to Proxy in that both buffer a com­plex enti­ty and ini­tial­ize it on its own. Unlike Facade, Proxy has the same inter­face as its ser­vice object, which makes them inter­change­able.

▪ Chain of Respon­si­bil­i­ty is a behav­ioral design pat­tern that lets you pass requests along a chain of han­dlers. Upon receiv­ing a request, each han­dler decides either to process the request or to pass it to the next han­dler in the chain.

▪ Like many other behav­ioral design pat­terns, the Chain of Respon­si­bil­i­ty relies on trans­form­ing par­tic­u­lar behav­iors into stand-alone objects called han­dlers.

▪ The pat­tern sug­gests that you link these han­dlers into a chain. Each linked han­dler has a field for stor­ing a ref­er­ence to the next han­dler in the chain. In addi­tion to pro­cess­ing a request, han­dlers pass the request fur­ther along the chain. The request trav­els along the chain until all han­dlers have had a chance to process it.

▪ Here’s the best part: a han­dler can decide not to pass the request fur­ther down the chain and effec­tive­ly stop any fur­ther processing.

▪ For instance, when a user clicks a but­ton, the event prop­a­gates through the chain of GUI ele­ments that starts with the but­ton, goes along its con­tain­ers (like forms or pan­els), and ends up with the main appli­ca­tion win­dow. The event is processed by the first ele­ment in the chain that’s capa­ble of han­dling it. This exam­ple is also note­wor­thy because it shows that a chain can always be extract­ed from an object tree.

▪ The Base Han­dler is an option­al class where you can put the boil­er­plate code that’s com­mon to all han­dler classes.

▪ Usu­al­ly, this class defines a field for stor­ing a ref­er­ence to the next han­dler. The clients can build a chain by pass­ing a han­dler to the con­struc­tor or set­ter of the pre­vi­ous han­dler.

▪ In this exam­ple, the Chain of Respon­si­bil­i­ty pat­tern is respon­si­ble for dis­play­ing con­tex­tu­al help infor­ma­tion for active GUI elements.

▪ The GUI class­es are built with the Com­pos­ite pat­tern. Each ele­ment is linked to its con­tain­er ele­ment. At any point, you can build a chain of ele­ments that starts with the ele­ment itself and goes through all of its con­tain­er elements.

▪ Use the Chain of Respon­si­bil­i­ty pat­tern when your pro­gram is expect­ed to process dif­fer­ent kinds of requests in var­i­ous ways, but the exact types of requests and their sequences are unknown beforehand.

▪ The pat­tern lets you link sev­er­al han­dlers into one chain and, upon receiv­ing a request, “ask” each han­dler whether it can process it. This way all han­dlers get a chance to process the request.

▪ Use the CoR pat­tern when the set of han­dlers and their order are sup­posed to change at runtime

▪ Decide how the client will pass the request data into the method. The most flex­i­ble way is to con­vert the request into an object and pass it to the han­dling method as an argument.

▪ You can also imple­ment the con­ve­nient default behav­ior for the han­dling method, which is to for­ward the request to the next object unless there’s none left.

▪ Sin­gle Respon­si­bil­i­ty Prin­ci­ple. You can decou­ple class­es that invoke oper­a­tions from class­es that per­form operations.

▪ Open/Closed Prin­ci­ple. You can intro­duce new han­dlers into the app with­out break­ing the exist­ing client code.
Some requests may end up unhandled.

▪ Chain of Respon­si­bil­i­ty pass­es a request sequen­tial­ly along a dynam­ic chain of poten­tial receivers until one of them han­dles it.

▪ Com­mand estab­lish­es uni­di­rec­tion­al con­nec­tions between senders and receivers.

▪ Medi­a­tor elim­i­nates direct con­nec­tions between senders and receivers, forc­ing them to com­mu­ni­cate indi­rect­ly via a medi­a­tor object.

▪ Observ­er lets receivers dynam­i­cal­ly sub­scribe to and unsub­scribe from receiv­ing requests.

▪ Chain of Respon­si­bil­i­ty is often used in con­junc­tion with Com­pos­ite.

▪ In this case, you can exe­cute a lot of dif­fer­ent oper­a­tions over the same con­text object, rep­re­sent­ed by a request.

▪ Com­mand is a behav­ioral design pat­tern that turns a request into a stand-alone object that con­tains all infor­ma­tion about the request. This trans­for­ma­tion lets you pass requests as a method argu­ments, delay or queue a request’s exe­cu­tion, and sup­port undoable operations.

▪ Good soft­ware design is often based on the prin­ci­ple of sep­a­ra­tion of con­cerns, which usu­al­ly results in break­ing an app into lay­ers. The most com­mon exam­ple: a layer for the graph­i­cal user inter­face and anoth­er layer for the busi­ness logic.

▪ How­ev­er, when it comes to doing some­thing impor­tant, like cal­cu­lat­ing the tra­jec­to­ry of the moon or com­pos­ing an annu­al report, the GUI layer del­e­gates the work to the under­ly­ing layer of busi­ness logic.

▪ The Com­mand pat­tern sug­gests that GUI objects shouldn’t send these requests direct­ly. Instead, you should extract all of the request details, such as the object being called, the name of the method and the list of argu­ments into a sep­a­rate com­mand class with a sin­gle method that trig­gers this request.

▪ As a result, com­mands become a con­ve­nient mid­dle layer that reduces cou­pling between the GUI and busi­ness logic lay­ers.

▪ The paper order serves as a com­mand. It remains in a queue until the chef is ready to serve it. The order con­tains all the rel­e­vant infor­ma­tion required to cook the meal. It allows the chef to start cook­ing right away instead of run­ning around clar­i­fy­ing the order details from you directly.

▪ The Com­mand pat­tern can turn a spe­cif­ic method call into a stand-alone object. This change opens up a lot of inter­est­ing uses: you can pass com­mands as method argu­ments, store them inside other objects, switch linked com­mands at run­time, etc.

▪ Use the Com­mand pat­tern when you want to queue oper­a­tions, sched­ule their exe­cu­tion, or exe­cute them remotely.

▪ As with any other object, a com­mand can be seri­al­ized, which means con­vert­ing it to a string that can be eas­i­ly writ­ten to a file or a data­base. Later, the string can be restored as the ini­tial com­mand object. Thus, you can delay and sched­ule com­mand exe­cu­tion. But there’s even more! In the same way, you can queue, log or send com­mands over the network.

▪ Use the Com­mand pat­tern when you want to imple­ment reversible operations.

▪ Although there are many ways to imple­ment undo/redo, the Com­mand pat­tern is per­haps the most pop­u­lar of all.

▪ This method has two draw­backs. First, it isn’t that easy to save an appli­ca­tion’s state because some of it can be pri­vate. This prob­lem can be mit­i­gat­ed with the Memen­to pattern.

▪ Sec­ond, the state back­ups may con­sume quite a lot of RAM. There­fore, some­times you can resort to an alter­na­tive imple­men­ta­tion: instead of restor­ing the past state, the com­mand per­forms the inverse oper­a­tion. The reverse oper­a­tion also has a price: it may turn out to be hard or even impos­si­ble to implement.

▪ Chain of Respon­si­bil­i­ty, Com­mand, Medi­a­tor and Observ­er address var­i­ous ways of con­nect­ing senders and receivers of requests:

▪ Com­mand estab­lish­es uni­di­rec­tion­al con­nec­tions between senders and receivers.

▪ How­ev­er, there’s anoth­er approach, where the request itself is a Com­mand object. In this case, you can exe­cute the same oper­a­tion in a series of dif­fer­ent con­texts linked into a chain.

▪ Com­mand and Strat­e­gy may look sim­i­lar because you can use both to para­me­ter­ize an object with some action. How­ev­er, they have very dif­fer­ent intents.

▪ Iter­a­tor is a behav­ioral design pat­tern that lets you tra­verse ele­ments of a col­lec­tion with­out expos­ing its under­ly­ing rep­re­sen­ta­tion (list, stack, tree, etc.).

▪ The main idea of the Iter­a­tor pat­tern is to extract the tra­ver­sal behav­ior of a col­lec­tion into a sep­a­rate object called an iter­a­tor.

▪ In addi­tion to imple­ment­ing the algo­rithm itself, an iter­a­tor object encap­su­lates all of the tra­ver­sal details, such as the cur­rent posi­tion and how many ele­ments are left till the end. Because of this, sev­er­al iter­a­tors can go through the same col­lec­tion at the same time, inde­pen­dent­ly of each other.

▪ The Iter­a­tor inter­face declares the oper­a­tions required for tra­vers­ing a col­lec­tion: fetch­ing the next ele­ment, retriev­ing the cur­rent posi­tion, restart­ing iter­a­tion, etc.

▪ Con­crete Iter­a­tors imple­ment spe­cif­ic algo­rithms for tra­vers­ing a col­lec­tion. The iter­a­tor object should track the tra­ver­sal progress on its own. This allows sev­er­al iter­a­tors to tra­verse the same col­lec­tion inde­pen­dent­ly of each other.

▪ Use the Iter­a­tor pat­tern when your col­lec­tion has a com­plex data struc­ture under the hood, but you want to hide its com­plex­i­ty from clients (either for con­ve­nience or secu­ri­ty reasons).

▪ Use the pat­tern to reduce dupli­ca­tion of the tra­ver­sal code across your app.

▪ The code of non-triv­ial iter­a­tion algo­rithms tends to be very bulky. When placed with­in the busi­ness logic of an app, it may blur the respon­si­bil­i­ty of the orig­i­nal code and make it less main­tain­able. Mov­ing the tra­ver­sal code to des­ig­nat­ed iter­a­tors can help you make the code of the appli­ca­tion more lean and clean.

▪ Use the Iter­a­tor when you want your code to be able to tra­verse dif­fer­ent data struc­tures or when types of these struc­tures are unknown beforehand.

▪ Apply­ing the pat­tern can be an overkill if your app only works with sim­ple collections.

▪ Mediator 

Also known as: Intermediary, Controller

▪ Medi­a­tor is a behav­ioral design pat­tern that lets you reduce chaot­ic depen­den­cies between objects

▪ The pat­tern restricts direct com­mu­ni­ca­tions between the objects and forces them to col­lab­o­rate only via a medi­a­tor object.

▪ Rela­tions between ele­ments of the user inter­face can become chaot­ic as the appli­ca­tion evolves.

▪ The Medi­a­tor pat­tern sug­gests that you should cease all direct com­mu­ni­ca­tion between the com­po­nents which you want to make inde­pen­dent of each other. Instead, these com­po­nents must col­lab­o­rate indi­rect­ly, by call­ing a spe­cial medi­a­tor object that redi­rects the calls to appro­pri­ate com­po­nents. As a result, the com­po­nents depend only on a sin­gle medi­a­tor class instead of being cou­pled to dozens of their colleagues.

▪ UI ele­ments should com­mu­ni­cate indi­rect­ly, via the medi­a­tor object.

▪ Let’s con­sid­er the sub­mit but­ton. Pre­vi­ous­ly, each time a user clicked the but­ton, it had to val­i­date the val­ues of all indi­vid­ual form ele­ments. Now its sin­gle job is to noti­fy the dia­log about the click. Upon receiv­ing this noti­fi­ca­tion, the dia­log itself per­forms the val­i­da­tions or pass­es the task to the indi­vid­ual ele­ments. Thus, instead of being tied to a dozen form ele­ments, the but­ton is only depen­dent on the dia­log class.

▪ This way, the Medi­a­tor pat­tern lets you encap­su­late a com­plex web of rela­tions between var­i­ous objects inside a sin­gle medi­a­tor object

▪ The fewer depen­den­cies a class has, the eas­i­er it becomes to mod­i­fy, extend or reuse that class.

▪ Air­craft pilots don’t talk to each other direct­ly when decid­ing who gets to land their plane next. All com­mu­ni­ca­tion goes through the con­trol tower.

▪ With­out the air traf­fic con­troller, pilots would need to be aware of every plane in the vicin­i­ty of the air­port, dis­cussing land­ing pri­or­i­ties with a com­mit­tee of dozens of other pilots. That would prob­a­bly sky­rock­et the air­plane crash statistics.

▪ The tower doesn’t need to con­trol the whole flight. It exists only to enforce con­straints in the ter­mi­nal area because the num­ber of involved actors there might be over­whelm­ing to a pilot.

▪ Com­po­nents are var­i­ous class­es that con­tain some busi­ness logic. Each com­po­nent has a ref­er­ence to a medi­a­tor, declared with the type of the medi­a­tor inter­face. The com­po­nent isn’t aware of the actu­al class of the medi­a­tor, so you can reuse the com­po­nent in other pro­grams by link­ing it to a dif­fer­ent mediator.

▪ The Medi­a­tor inter­face declares meth­ods of com­mu­ni­ca­tion with com­po­nents, which usu­al­ly include just a sin­gle noti­fi­ca­tion method

▪ Com­po­nents must not be aware of other com­po­nents. If some­thing impor­tant hap­pens with­in or to a com­po­nent, it must only noti­fy the medi­a­tor.

▪ From a com­po­nent’s per­spec­tive, it all looks like a total black box. The sender doesn’t know who’ll end up han­dling its request, and the receiv­er doesn’t know who sent the request in the first place.

▪ In this exam­ple, the Medi­a­tor pat­tern helps you elim­i­nate mutu­al depen­den­cies between var­i­ous UI class­es: but­tons, check­box­es and text labels.

▪ The pat­tern lets you extract all the rela­tion­ships between class­es into a sep­a­rate class, iso­lat­ing any changes to a spe­cif­ic com­po­nent from the rest of the components.

▪ Medi­a­tor, indi­vid­ual com­po­nents become unaware of the other com­po­nents. They could still com­mu­ni­cate with each other, albeit indi­rect­ly, through a medi­a­tor object

▪ Chain of Respon­si­bil­i­ty pass­es a request sequen­tial­ly along a dynam­ic chain of poten­tial receivers until one of them han­dles it.

▪ Facade and Medi­a­tor have sim­i­lar jobs: they try to orga­nize col­lab­o­ra­tion between lots of tight­ly cou­pled classes.

▪ The dif­fer­ence between Medi­a­tor and Observ­er is often elu­sive. In most cases, you can imple­ment either of these pat­terns; but some­times you can apply both simul­ta­ne­ous­ly.

▪ When you’re con­fused, remem­ber that you can imple­ment the Medi­a­tor pat­tern in other ways. For exam­ple, you can per­ma­nent­ly link all the com­po­nents to the same medi­a­tor object. This imple­men­ta­tion won’t resem­ble Observ­er but will still be an instance of the Medi­a­tor pattern.

▪ Memento 

Also known as: Snapshot

▪ Memen­to is a behav­ioral design pat­tern that lets you save and restore the pre­vi­ous state of an object with­out reveal­ing the details of its imple­men­ta­tion.

▪ Before exe­cut­ing an oper­a­tion, the app saves a snap­shot of the objects’ state, which can later be used to restore objects to their pre­vi­ous state.

▪ The Memen­to pat­tern del­e­gates cre­at­ing the state snap­shots to the actu­al owner of that state, the orig­i­na­tor object. Hence, instead of other objects try­ing to copy the edi­tor’s state from the “out­side,” the edi­tor class itself can make the snap­shot since it has full access to its own state.

▪ The pat­tern sug­gests stor­ing the copy of the object’s state in a spe­cial object called memen­to. The con­tents of the memen­to aren’t acces­si­ble to any other object except the one that pro­duced it. Other objects must com­mu­ni­cate with memen­tos using a lim­it­ed inter­face which may allow fetch­ing the snap­shot’s meta­da­ta (cre­ation time, the name of the per­formed oper­a­tion, etc.), but not the orig­i­nal object’s state con­tained in the snapshot.

▪ The orig­i­na­tor has full access to the memen­to, where­as the care­tak­er can only access the metadata.

▪ While most peo­ple remem­ber this pat­tern thanks to the “undo” use case, it’s also indis­pens­able when deal­ing with trans­ac­tions (i.e., if you need to roll back an oper­a­tion on error).

▪ Most dynam­ic pro­gram­ming lan­guages, such as PHP, Python and JavaScript, can’t guar­an­tee that the state with­in the memen­to stays untouched.

▪ Some­times Pro­to­type can be a sim­pler alter­na­tive to Memen­to. This works if the object, the state of which you want to store in the his­to­ry, is fair­ly straight­for­ward and doesn’t have links to exter­nal resources, or the links are easy to re-estab­lish.

▪ Also known as: Event-Subscriber, Listener

▪ Observ­er is a behav­ioral design pat­tern that lets you define a sub­scrip­tion mech­a­nism to noti­fy mul­ti­ple objects about any events that hap­pen to the object they’re observing.

▪ The object that has some inter­est­ing state is often called sub­ject, but since it’s also going to noti­fy other objects about the changes to its state, we’ll call it pub­lish­er. All other objects that want to track changes to the pub­lish­er’s state are called sub­scribers.

▪ The pub­lish­er main­tains a list of sub­scribers and knows which mag­a­zines they’re inter­est­ed in. Sub­scribers can leave the list at any time when they wish to stop the pub­lish­er send­ing new mag­a­zine issues to them.

▪ The list of sub­scribers is com­piled dynam­i­cal­ly: objects can start or stop lis­ten­ing to noti­fi­ca­tions at run­time, depend­ing on the desired behav­ior of your app.

▪ Use the Observ­er pat­tern when changes to the state of one object may require chang­ing other objects, and the actu­al set of objects is unknown before­hand or changes dynamically.

▪ For exam­ple, you cre­at­ed cus­tom but­ton class­es, and you want to let the clients hook some cus­tom code to your but­tons so that it fires when­ev­er a user press­es a button.

The Observ­er pat­tern lets any object that imple­ments the sub­scriber inter­face sub­scribe for event noti­fi­ca­tions in pub­lish­er objects. You can add the sub­scrip­tion mech­a­nism to your but­tons, let­ting the clients hook up their cus­tom code via cus­tom sub­scriber classes.

▪ Use the pat­tern when some objects in your app must observe oth­ers, but only for a lim­it­ed time or in spe­cif­ic cases.

▪ The dif­fer­ence between Medi­a­tor and Observ­er is often elu­sive. In most cases, you can imple­ment either of these pat­terns; but some­times you can apply both simul­ta­ne­ous­ly.

▪ The pri­ma­ry goal of Medi­a­tor is to elim­i­nate mutu­al depen­den­cies among a set of sys­tem com­po­nents. Instead, these com­po­nents become depen­dent on a sin­gle medi­a­tor object. The goal of Observ­er is to estab­lish dynam­ic one-way con­nec­tions between objects, where some objects act as sub­or­di­nates of others.

▪ The State pat­tern is close­ly relat­ed to the con­cept of a Finite-State Machine 10.

▪ The main idea is that, at any given moment, there’s a finite num­ber of states which a pro­gram can be

▪ State machines are usu­al­ly imple­ment­ed with lots of con­di­tion­al state­ments (if or switch) that select the appro­pri­ate behav­ior depend­ing on the cur­rent state of the object

▪ Usu­al­ly, this “state” is just a set of val­ues of the object’s fields. Even if you’ve never heard about finite-state machines before, you’ve prob­a­bly imple­ment­ed a state at least once.

▪ The State pat­tern sug­gests that you cre­ate new class­es for all pos­si­ble states of an object and extract all state-spe­cif­ic behav­iors into these classes

▪ This struc­ture may look sim­i­lar to the Strat­e­gy pat­tern, but there’s one key dif­fer­ence. In the State pat­tern, the par­tic­u­lar states may be aware of each other and ini­ti­ate tran­si­tions from one state to anoth­er, where­as strate­gies almost never know about each other.

▪ The but­tons and switch­es in your smart­phone behave dif­fer­ent­ly depend­ing on the cur­rent state of the device:

When the phone is unlocked, press­ing but­tons leads to exe­cut­ing var­i­ous functions.
When the phone is locked, press­ing any but­ton leads to the unlock screen.
When the phone’s charge is low, press­ing any but­ton shows the charg­ing screen

▪ In this exam­ple, the State pat­tern lets the same con­trols of the media play­er behave dif­fer­ent­ly, depend­ing on the cur­rent play­back state.

▪ Use the State pat­tern when you have an object that behaves dif­fer­ent­ly depend­ing on its cur­rent state, the num­ber of states is enor­mous, and the state-spe­cif­ic code changes frequently.

▪ Bridge, State, Strat­e­gy (and to some degree Adapter) have very sim­i­lar struc­tures. Indeed, all of these pat­terns are based on com­po­si­tion, which is del­e­gat­ing work to other objects.

▪ A pat­tern isn’t just a recipe for struc­tur­ing your code in a spe­cif­ic way. It can also com­mu­ni­cate to other devel­op­ers the prob­lem the pat­tern solves.

▪ State can be con­sid­ered as an exten­sion of Strat­e­gy. Both pat­terns are based on com­po­si­tion: they change the behav­ior of the con­text by del­e­gat­ing some work to helper objects. Strat­e­gy makes these objects com­plete­ly inde­pen­dent and unaware of each other. How­ev­er, State doesn’t restrict depen­den­cies between con­crete states, let­ting them alter the state of the con­text at will.

▪ In addi­tion, team­work became inef­fi­cient. Your team­mates, who had been hired right after the suc­cess­ful release, com­plain that they spend too much time resolv­ing merge con­flicts. Imple­ment­ing a new fea­ture requires you to change the same huge class, con­flict­ing with the code pro­duced by other people.

▪ The Strat­e­gy pat­tern sug­gests that you take a class that does some­thing spe­cif­ic in a lot of dif­fer­ent ways and extract all of these algo­rithms into sep­a­rate class­es called strate­gies.

▪ The orig­i­nal class, called con­text, must have a field for stor­ing a ref­er­ence to one of the strate­gies. The con­text del­e­gates the work to a linked strat­e­gy object instead of exe­cut­ing it on its own.

▪ The con­text isn’t respon­si­ble for select­ing an appro­pri­ate algo­rithm for the job. Instead, the client pass­es the desired strat­e­gy to the con­text. In fact, the con­text doesn’t know much about strate­gies. It works with all strate­gies through the same gener­ic inter­face, which only expos­es a sin­gle method for trig­ger­ing the algo­rithm encap­su­lat­ed with­in the select­ed strategy.

▪ This way the con­text becomes inde­pen­dent of con­crete strate­gies, so you can add new algo­rithms or mod­i­fy exist­ing ones with­out chang­ing the code of the con­text or other strategies.

▪ The client code picks a concrete strategy and passes it to
// the context. The client should be aware of the differences
// between strategies in order to make the right choice.

▪ Use the Strat­e­gy pat­tern when you want to use dif­fer­ent vari­ants of an algo­rithm with­in an object and be able to switch from one algo­rithm to anoth­er dur­ing runtime.

▪ You can iso­late the imple­men­ta­tion details of an algo­rithm from the code that uses it.
You can replace inher­i­tance with composition.

▪ A lot of mod­ern pro­gram­ming lan­guages have func­tion­al type sup­port that lets you imple­ment dif­fer­ent ver­sions of an algo­rithm inside a set of anony­mous func­tions. Then you could use these func­tions exact­ly as you’d have used the strat­e­gy objects, but with­out bloat­ing your code with extra class­es and interfaces.

▪ Bridge, State, Strat­e­gy (and to some degree Adapter) have very sim­i­lar struc­tures. Indeed, all of these pat­terns are based on com­po­si­tion, which is del­e­gat­ing work to other objects.

▪ At some point, you noticed that all three class­es have a lot of sim­i­lar code. While the code for deal­ing with var­i­ous data for­mats was entire­ly dif­fer­ent in all class­es, the code for data pro­cess­ing and analy­sis is almost iden­ti­cal. Wouldn’t it be great to get rid of the code dupli­ca­tion, leav­ing the algo­rithm struc­ture intact?

▪ There’s anoth­er type of step, called hooks. A hook is an option­al step with an empty body. A tem­plate method would work even if a hook isn’t over­rid­den. Usu­al­ly, hooks are placed before and after cru­cial steps of algo­rithms, pro­vid­ing sub­class­es with addi­tion­al exten­sion points for an algorithm.

▪ The tem­plate method approach can be used in mass hous­ing con­struc­tion. The archi­tec­tur­al plan for build­ing a stan­dard house may con­tain sev­er­al exten­sion points that would let a poten­tial owner adjust some details of the result­ing house.

▪ Each build­ing step, such as lay­ing the foun­da­tion, fram­ing, build­ing walls, installing plumb­ing and wiring for water and elec­tric­i­ty, etc., can be slight­ly changed to make the result­ing house a lit­tle bit dif­fer­ent from others.

▪ All races in the game have almost the same types of units and build­ings. There­fore you can reuse the same AI struc­ture for var­i­ous races, while being able to over­ride some of the details. With this approach, you can over­ride the orcs’ AI to make it more aggres­sive, make humans more defense-ori­ent­ed, and make mon­sters unable to build any­thing. Adding a new race to the game would require cre­at­ing a new AI sub­class and over­rid­ing the default meth­ods declared in the base AI class.

▪ Use the Tem­plate Method pat­tern when you want to let clients extend only par­tic­u­lar steps of an algo­rithm, but not the whole algo­rithm or its structure.

▪ Tem­plate meth­ods tend to be hard­er to main­tain the more steps they have.

▪ Fac­to­ry Method is a spe­cial­iza­tion of Tem­plate Method. At the same time, a Fac­to­ry Method may serve as a step in a large Tem­plate Method.

▪ Tem­plate Method is based on inher­i­tance: it lets you alter parts of an algo­rithm by extend­ing those parts in sub­class­es. Strat­e­gy is based on com­po­si­tion: you can alter parts of the object’s behav­ior by sup­ply­ing it with dif­fer­ent strate­gies that cor­re­spond to that behav­ior.

▪ Tem­plate Method works at the class level, so it’s sta­t­ic. Strat­e­gy works on the object level, let­ting you switch behav­iors at runtime.

▪ Vis­i­tor is a behav­ioral design pat­tern that lets you sep­a­rate algo­rithms from the objects on which they operate

▪ How­ev­er, the Vis­i­tor pat­tern address­es this prob­lem. It uses a tech­nique called Dou­ble Dis­patch, which helps to exe­cute the prop­er method on an object with­out cum­ber­some con­di­tion­als.

▪ The Vis­i­tor inter­face declares a set of vis­it­ing meth­ods that can take con­crete ele­ments of an object struc­ture as argu­ments.

▪ Use the Vis­i­tor when you need to per­form an oper­a­tion on all ele­ments of a com­plex object struc­ture (for exam­ple, an object tree).

▪ The Vis­i­tor pat­tern lets you exe­cute an oper­a­tion over a set of objects with dif­fer­ent class­es by hav­ing a vis­i­tor object imple­ment sev­er­al vari­ants of the same oper­a­tion, which cor­re­spond to all tar­get classes.

▪ Declare the vis­i­tor inter­face with a set of “vis­it­ing” meth­ods, one per each con­crete ele­ment class that exists in the program

▪ The ele­ment class­es should only work with vis­i­tors via the vis­i­tor inter­face. Vis­i­tors, how­ev­er, must be aware of all con­crete ele­ment class­es, ref­er­enced as para­me­ter types of the vis­it­ing methods.

▪ Joshua Kerievsky’s book Refac­tor­ing To Pat­terns:
https://refac­tor­ing.guru/ref-to-pat­terns-book

▪ Dive Into Refac­tor­ing:
https://refac­tor­ing.guru/refac­tor­ing/course
