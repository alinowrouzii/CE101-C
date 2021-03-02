## شبیه‌سازی تعقیب دزد توسط پلیس‌ها

### تعریف مساله

هدف از اين برنامه شبيه‌سازی تعقيب یک دزد توسط چندين پليس است. در اين شبيه‌سازی، محيط تعقيب و گريز!!! و زمان گسسته هستند. محيط به صورت يك ماتريس n x m در نظر گرفته می‌شود و زمان با يک متغير گسسته (مثلا  int) توصيف می‌شود. یعنی در ابتدا زمان 0 است سپس 1 می‌شود، بعد 2 و ....

در طول شبيه‌سازی، در هر لحظه t، هم دزد و هم پليس‌ها تصميم‌ ‌می‌گیرند كه در زمان t+1 در چه محلی (چه خانه‌ای از ماتريس باشند). بعد از اينكه همه اين تصميم‌گيری‌ها انجام شد، زمان يك واحد افزايش می‌يابد و محل دزد‌ و پليس‌ها بر اساس تصميمات گرفته شده تغيير پيدا می‌كند. اين فرايند تا زمانی تكرار ‌می‌شود كه پليس‌ها دزد را بگيرند!!!

تصميم‌گيری دزد به اين صورت است كه اگر در زمان t، دزد كه در محل (x,y) قرار داشته باشد تصميم می‌گيرد كه در زمان t+1 به صورت تصادفی به يك خانه همسايه مثلا  (x + 1, y) يا (x - 1, y + 1) يا (x, y) يا ... برود.

تصميم‌گیری پليس‌ها هم به اين صورت است كه  در زمان t ابتدا بررسی می‌كنند كه آيا از محل دزد اطلاع دارند يا نه. اگر اطلاع نداشته باشند مانند دزد به صورت كاملا تصادفی حركت می‌كنند در غير اين صورت، يک خانه به طرف محل دزد حركت می‌كنند.

پليس‌ها به دو نحوه می‌توانند از محل دزد آگاه شوند. يا اينكه خودشان دزد را ببینند يا اينكه يكی از پليس‌های ديگر كه دزد را ديده است به آنها اطلاع می‌دهد. هر پليس‌ زمانی دزد را می‌بيند كه دزد در يكی از همسايه‌های تا دو گام آن باشد. برای مثال اگر پليس در محل (x,y) باشد و دزد در محل (x + 2, y -2) يا (x – 1, y) باشد، پليس دزد را می‌بيند. ولی اگر دزد در خانه (x + 3, y) يا (x + 1, y + 4) باشد پليس آن را نمی‌بيند. محدوده ديد پليس در شكل نشان داده شده است.

| ستون 1 | ستون 2 | ستون 3 | ستون 4 | ستون 5 |
| ------ | ------ | ------ | ------ | ------ |
|        |        |        |        |        |
|        |        |        |        |        |
|        |        | (x,y) |        |        |
|        |        |        |        |        |
|        |        |        |        |        |

پليس‌ها زمانی دزد را می‌گيرند كه خانه يكی از پليس‌ها و دزد يكی شود. يا اينكه دزد در زمان t+1 به خانه (x,y) بيايد كه در زمان t پليس در آن بود. (دزد خود به آغوش پليس آيد!!)

اين برنامه بايد ماتريس محيط شبيه‌سازی، محل دزد (با حرف D) و محل پليس‌ها (با حرف P) را در هر زمان شبيه‌سازی نشان دهد. در انتهای برنامه تعداد حركت‌های دزد و مجموع كل حركت‌های پليس‌ها را چاپ كند.

### نکات پیاده‌سازی

1) اندازه محيط شبيه‌سازی از كاربر پرسيده می‌شود.

2) تعداد پليس‌ها از كاربر پرسيده می‌شود.

3) محل اوليه دزد‌ها و پليس‌ها به صورت تصادفی انتخاب می‌شود (واضح است كه در يك خانه دو نفر نمی‌توانند همزمان وجود داشته باشند)

4) واضح است كه نبايد دزد يا پليس از محيط شبيه‌سازی خارج شود.

5) اگر برنامه شما، ماتريس محيط شبيه‌سازي را در زمان‌هاي t و t+1 و t+2 و ... بدون هيچ تاخيري چاپ كند، عملا كاربر متوجه نمی‌شود كه چه اتفاقی افتاده است. بنابراين در هر زمان t بعد از اينكه تصمیم‌گیری‌ها انجام شد، قبل از اينكه به زمان t+1 برويم و مكان‌ها را تغيير دهيد. به اندازه مثلا  0.5 ثانيه صبر كنيد. براي اين كار مي‌توانيد از دستور زير استفاده كنيد.

    #include <stdlib.h>
    
    sleep(500);

6) در هر لحظه زمانی، قبل از اينكه محيط شبيه‌سازی را رسم كنيد. صفحه كنسول را با دستورات زير پاک نماييد.

    #include <stdlib.h>
    
    system("cls");

7) (اختياری) دزد هم می‌تواند پليس‌ها را ببیند و در صورتي كه پليسی را ببيند، سعی می‌کند از دست وی فرار كند!!