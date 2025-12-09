---
name: lpic
lesson: "10"
topic: package management
number: "10"
---
we have a mirrorlist file and it's configuration files are different from vary distributes.
- ### Debian
	#apt-get and #apt and #dpkg 
	#apt and #apt-get both are package manager in debian which look to mirrorlist and use those mirrors to update, download, search, etc.
	#dpkg is a tool to install #deb  files.
	- you can find #mirror and #apt configs in #/etc/apt/ directory
- ### RPM and YUM in redhats
  in #redhats we have #yum, #dnf package managers
  `we don't deepin redhats and debians yet!`
  - #rpm:
	  #-i -> install packagename.rpm
	  #-U -> if package has installed, it upgrades it, unless install it
	  #-e -> earase, means remove the package from system
	  - query in #RPM:
		  #-q -> used to send query with it's switches
		  #-qi -> information of package
		  #-qc -> packages configuration files
		  #-qa -> shows all installed packages
		  #-qR -> dependencies of a package requires
		  #-qf -> shows package owning file
		  #-ql -> lists the files of a package installs
- ### Pacman (Arch based)
	this is my favorite so let's learn it:
	pacman categorize packages which installed in 2 category:
	1- #packages which are installed by `pacman -S`or`pacman -U file.zst`
	2- #packages which are installed as #dependency cause they are required by other packages.
	- ##### switches:
	#-S -> `pacman -S package1 package2 ...` to install packages
	#-R ->`pacman -R pkgname`only unistall and remove package not it's dependencies and configuration files.
	#-Rs -> `pacman -Rs pkgname`removes package and it's dependecies
	#-Rns ->`pacman -Rns pkgname`remove package and it's depencies and configuration files.
	#-Syu ->`pacman -Syu`updating the system and packages:
		#-S -> synchronize the database
		#-y -> refresh local cache
		#-u -> system update
		#how_it_works? your arch synchronize which mirrors and then refresh your local cache with new value and then run system update.
	#-Q -> to see all packages 
		#-Qs -> `pacman -Qs zsh tmux` -> esearching for one or multiple package
	#-F ->`pacman -F pkgname`-> search the pkgname in local database.
	#-Ss -> `pacman -Ss pkgname`-> search the repos(mirrors) to your package name.
	#paccache ->`paccache -r` -> to remove pacman cache
	#pactree -> `pactree zsh` -> shows a tree of zsh require dependencies.
	- ==how to install unofficial packages==?
	- #-U -> `pacman -U packagename.pkg.tar.xz` -> install th `pkg.tar.xz` file for arch.
	- #-U -> `pacman -U https://adjnneneffe/sfe/fefe/ex.pkg.tar.xz` -> install remove packages which is not from official repo and mirror.
	- #Qi -> `pacman -Qi packagename` -> to see package information








put out fire
خاموش کردن اتش
4
11/5/2025
Review in 14 days. You're doing well!
cut down
قطع کردن
4
11/5/2025
Review in 14 days. You're doing well!
endangered
در معرض خطر. در خطر
4
11/5/2025
Review in 14 days. You're doing well!
plain
دشت. طبیعت
4
11/5/2025
Review in 14 days. You're doing well!
halve
نصف
3
10/29/2025
Review in 7 days. Keep it up!
zookeeper
نگهبان باغ وحش
3
10/29/2025
Review in 7 days. Keep it up!
giraffe
زرافه
3
10/29/2025
Review in 7 days. Keep it up!
hen
مرغ
3
10/29/2025
Review in 7 days. Keep it up!
wolves
گرگ ها
3
10/29/2025
Review in 7 days. Keep it up!
proper
مناسب. مخصوص
2
10/25/2025
Review in 3 days. Good progress!
identity
هویت
4
11/5/2025
Review in 14 days. You're doing well!
plant
گیاه
3
10/29/2025
Review in 7 days. Keep it up!
observatory
رصدخانه
3
10/29/2025
Review in 7 days. Keep it up!
orbit
دایره شکل. مدار. حلقه
3
10/29/2025
Review in 7 days. Keep it up!
metal
اهنی
3
10/29/2025
Review in 7 days. Keep it up!
mars
مریخ
2
10/25/2025
Review in 3 days. Good progress!
saturn
زحل
2
10/25/2025
Review in 3 days. Good progress!
mercury
مشتری
4
11/5/2025
Review in 14 days. You're doing well!
jupiter
مشتری
4
11/5/2025
Review in 14 days. You're doing well!
round
گرد.  دور زدن
1
10/23/2025
Review today! Stay focused.
down ward
رو به پایین
3
10/29/2025
Review in 7 days. Keep it up!
up ward
رو به بالا
3
10/29/2025
Review in 7 days. Keep it up!
abroad
خارج از کشور
4
11/5/2025
Review in 14 days. You're doing well!
wooden
چوبی
4
11/5/2025
Review in 14 days. You're doing well!
loudy
ابری
3
10/29/2025
Review in 7 days. Keep it up!
seafood
غذای دریایی
4
11/5/2025
Review in 14 days. You're doing well!
seek
جست و جو کردن
3
10/29/2025
Review in 7 days. Keep it up!
cradle
گهواره
3
10/29/2025
Review in 7 days. Keep it up!
grave
قبر
4
11/5/2025
Review in 14 days. You're doing well!
peace be upon him
درورد بر او
3
10/29/2025
Review in 7 days. Keep it up!
light bulb
لامپ
4
11/5/2025
Review in 14 days. You're doing well!
medicine
دارو . پزشکی
4
11/5/2025
Review in 14 days. You're doing well!
experiment
ازمایش
4
11/5/2025
Review in 14 days. You're doing well!
energetic
active
3
10/29/2025
Review in 7 days. Keep it up!
rapidly
fastly, fast
3
10/29/2025
Review in 7 days. Keep it up!
having flu
انفولانزا گرفتن
4
11/5/2025
Review in 14 days. You're doing well!
inventor
who invent sth
4
11/5/2025
Review in 14 days. You're doing well!
attend
مراجعه کردن به ...
4
11/5/2025
Review in 14 days. You're doing well!
after sth
دنبال .... گشتن
3
10/29/2025
Review in 7 days. Keep it up!
reciting
تلاوت کردن
3
10/29/2025
Review in 7 days. Keep it up!
pass away
died
4
11/5/2025
Review in 14 days. You're doing well!
patient
illness
3
10/29/2025
Review in 7 days. Keep it up!
novel
رمان
4
11/5/2025
Review in 14 days. You're doing well!
narrating
روایت کردن
1
10/23/2025
Review today! Stay focused.
emphasis
تاکید کردن
3
10/29/2025
Review in 7 days. Keep it up!
put sth aside
.... کنار گذاشتن
3
10/29/2025
Review in 7 days. Keep it up!
emotion
احساس
4
11/5/2025
Review in 14 days. You're doing well!
attraction
برجسته . جاذبه . کشندگی
2
10/25/2025
Review in 3 days. Good progress!
pilgrim
زاعر
3
10/29/2025
Review in 7 days. Keep it up!
booklet
کتابچه.  جزوه
3
10/29/2025
Review in 7 days. Keep it up!
historical
تاریخی
4
11/5/2025
Review in 14 days. You're doing well!
travel agent
اژانس مسافرتی
3
10/29/2025
Review in 7 days. Keep it up!
hospitable
مهمان نواز
3
10/29/2025
Review in 7 days. Keep it up!
pyramids
اهرام
3
10/29/2025
Review in 7 days. Keep it up!
ancient
باستانی
2
10/25/2025
Review in 3 days. Good progress!
entertainment
سرگرمی
3
10/29/2025
Review in 7 days. Keep it up!
continent
قاره
4
11/5/2025
Review in 14 days. You're doing well!
european
اروپایی
4
11/5/2025
Review in 14 days. You're doing well!
domestic
محلی . اهلی
3
10/29/2025
Review in 7 days. Keep it up!
wide
پهن . وسیع . گسترده
4
11/5/2025
Review in 14 days. You're doing well!
ceremony
مراسم
3
10/29/2025
Review in 7 days. Keep it up!
traditional
سنتی
4
11/5/2025
Review in 14 days. You're doing well!
embassy
سفارت
2
10/25/2025
Review in 3 days. Good progress!
agency
آژانس . نمایندگی
3
10/29/2025
Review in 7 days. Keep it up!
sunset
غروب خورشید
1
10/23/2025
Review today! Stay focused.
sunrise
طلوع خورشید
2
10/25/2025
Review in 3 days. Good progress!
obligations
الزامات
3
10/29/2025
Review in 7 days. Keep it up!
contract
قرارداد . عقد . توافق کردن
1
10/23/2025
Review today! Stay focused.
illness
بیماری . مرض. کسالت
3
10/29/2025
Review in 7 days. Keep it up!
prepare
اماده کردن
1
10/23/2025
Review today! Stay focused.
attract
جذب کردن
4
11/5/2025
Review in 14 days. You're doing well!
deaf
کر. ناشنوا
۳
10/29/2025
Review in 7 days. Keep it up!
familiar
اشنا بودن با چیزی
3
10/29/2025
Review in 7 days. Keep it up!
keep off
giving up of doing sth
3
10/29/2025
Review in 7 days. Keep it up!
according
براساس . با توجه به....
3
10/29/2025
Review in 7 days. Keep it up!
frequently
اغلب
2
10/25/2025
Review in 3 days. Good progress!
foreign
not native, not domestic
2
10/25/2025
Review in 3 days. Good progress!
besides
علاوه بر .... . در کنار ....
2
10/25/2025
Review in 3 days. Good progress!
fluently
easily
2
10/25/2025
Review in 3 days. Good progress!
to be honest
بخوام صادق باشم ....
3
10/29/2025
Review in 7 days. Keep it up!
institute
موسسه
4
11/5/2025
Review in 14 days. You're doing well!
region
منطقه
2
10/25/2025
Review in 3 days. Good progress!
century
100 years
3
10/29/2025
Review in 7 days. Keep it up!
meets the needs of...
نیاز هارا رفع میکند
3
10/29/2025
Review in 7 days. Keep it up!
by the means of..
از طریق....
2
10/25/2025
Review in 3 days. Good progress!
make up
تشکیل دادن . درست کردن
3
10/29/2025
Review in 7 days. Keep it up!
despite
علارقم
3
10/29/2025
Review in 7 days. Keep it up!
oceania
اقیانوسیه
3
10/29/2025
Review in 7 days. Keep it up!
passage
discuse, converstation
2
10/25/2025
Review in 3 days. Good progress!
belong
تعلق
3
10/29/2025
Review in 7 days. Keep it up!
a loaf of...
یه قرص ...
2
10/25/2025
Review in 3 days. Good progress!
bread
نان
4
11/5/2025
Review in 14 days. You're doing well!
measure
اندازه گیری
3
10/29/2025
Review in 7 days. Keep it up!
grade
نمره . امتیاز
3
10/29/2025
Review in 7 days. Keep it up!
surfing
searching
3
10/29/2025
Review in 7 days. Keep it up!
carrot
هویج
3
10/29/2025
Review in 7 days. Keep it up!
quince
به
3
10/29/2025
Review in 7 days. Keep it up!
rarely
به ندرت
3
10/29/2025
Review in 7 days. Keep it up!
gain weigth
اضافه وزن کردن
3
10/29/2025
Review in 7 days. Keep it up!
couch potato
چاق .
4
11/5/2025
Review in 14 days. You're doing well!
heartbeat
ضربان قلب
4
11/5/2025
Review in 14 days. You're doing well!
pressure
فشار
2
10/25/2025
Review in 3 days. Good progress!
behave
the approache of treating to sb
2
10/25/2025
Review in 3 days. Good progress!
towards
نسبت
2
10/25/2025
Review in 3 days. Good progress!
disease
بیماری . مرض. کسالت
2
10/25/2025
Review in 3 days. Good progress!
relative
اشنایان
3
10/29/2025
Review in 7 days. Keep it up!
predict
پیش بینی کردن
3
10/29/2025
Review in 7 days. Keep it up!
cure
مراقبت کردن
3
10/29/2025
Review in 7 days. Keep it up!
culture
فرهنگ
4
11/5/2025
Review in 14 days. You're doing well!
crafts
صنایع
3
10/29/2025
Review in 7 days. Keep it up!
handicrafts
صنایع دستی
3
10/29/2025
Review in 7 days. Keep it up!
pottery
سفال گری
1
10/23/2025
Review today! Stay focused.
tilework
کاشی کاری
3
10/29/2025
Review in 7 days. Keep it up!
calligraphy
قالی بافی
3
10/29/2025
Review in 7 days. Keep it up!
soft
نرم
3
10/29/2025
Review in 7 days. Keep it up!
how touching
چه تاثیر گذار
3
10/29/2025
Review in 7 days. Keep it up!
metal work
صنابع دستی اهنی
3
10/29/2025
Review in 7 days. Keep it up!
discount
تخفیف
3
10/29/2025
Review in 7 days. Keep it up!
decorative
دکوری
3
10/29/2025
Review in 7 days. Keep it up!
vast
پهن . وسیع . گسترده
3
10/29/2025
Review in 7 days. Keep it up!
craftsman
صنعتگر مرد
3
10/29/2025
Review in 7 days. Keep it up!
craftswoman
صنعتگر زن
3
10/29/2025
Review in 7 days. Keep it up!
weaving
بافتن
3
10/29/2025
Review in 7 days. Keep it up!
unique
منحصر به فرد
2
10/25/2025
Review in 3 days. Good progress!
diversity
متنوع
3
10/29/2025
Review in 7 days. Keep it up!
economy
اقتصاد
3
10/29/2025
Review in 7 days. Keep it up!
produce
تولید کردن
3
10/29/2025
Review in 7 days. Keep it up!
souvenir
سوغاتی
3
10/29/2025
Review in 7 days. Keep it up!
moral
اخلاق
3
10/29/2025
Review in 7 days. Keep it up!
silk
ابریشم
3
10/29/2025
Review in 7 days. Keep it up!
rug
قالیچه
3
10/29/2025
Review in 7 days. Keep it up!
homeland
وطن
3
10/29/2025
Review in 7 days. Keep it up!
frightened
ترسیده
2
10/25/2025
Review in 3 days. Good progress!
glad
خوشحال بودن
3
10/29/2025
Review in 7 days. Keep it up!
wellness
سلامتی
3
10/29/2025
Review in 7 days. Keep it up!
province
استان
2
10/25/2025
Review in 3 days. Good progress!
manner
روش
3
10/29/2025
Review in 7 days. Keep it up!
amused
سرگرم شد
3
10/29/2025
Review in 7 days. Keep it up!
amuse
سرگرم کردن
3
10/29/2025
Review in 7 days. Keep it up!
infinitive
مصدر
2
10/25/2025
Review in 3 days. Good progress!
frequent
مکرر
2
10/25/2025
Review in 3 days. Good progress!
preposition
حروف اضافه
1
10/23/2025
Review today! Stay focused.
influenced
تحت تاثیر قرار گرفت
1
10/23/2025
Review today! Stay focused.
recreational
تفریحی
1
10/23/2025
Review today! Stay focused.
mosque
مسجد
3
10/29/2025
Review in 7 days. Keep it up!
look after
مراقب بودن از....
2
10/25/2025
Review in 3 days. Good progress!
swing
تاب. تلو تلو خوردن. تاب خوردن
2
10/25/2025
Review in 3 days. Good progress!
bleed
خونریزی کردن
3
10/29/2025
Review in 7 days. Keep it up!
nearby
نزدیک
3
10/29/2025
Review in 7 days. Keep it up!
broadcast
پخش شدن
3
10/29/2025
Review in 7 days. Keep it up!
lend
قرض دادن
3
10/29/2025
Review in 7 days. Keep it up!
sink
فرو رفتن . غرق شدن
2
10/25/2025
Review in 3 days. Good progress!
look out
نگاه کن
3
10/29/2025
Review in 7 days. Keep it up!
miracle
معجزه
2
10/25/2025
Review in 3 days. Good progress!
specialist
متخصص
1
10/23/2025
Review today! Stay focused.
flat
تخت . صاف
2
10/25/2025
Review in 3 days. Good progress!
propotion
نسبت
1
10/23/2025
Review today! Stay focused.
vaccum cleaner
جاروبرقی
2
10/25/2025
Review in 3 days. Good progress!
impatient
بی حوصلگی . بد اخلق. بی توجه
1
10/23/2025
Review today! Stay focused.
mineral
معدنی
1
10/23/2025
Review today! Stay focused.
artifact
مصنوعی
3
10/29/2025
Review in 7 days. Keep it up!
therefore
thus
3
10/29/2025
Review in 7 days. Keep it up!
attitude
نگرش . روش و رفتار
1
10/23/2025
Review today! Stay focused.
transportation
ترابری . حمل و نقل
3
10/29/2025
Review in 7 days. Keep it up!





