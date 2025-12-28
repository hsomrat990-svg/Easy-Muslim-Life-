import 'package:flutter/material.dart';
import 'dart:async';

// ==========================================
// ১. ডাটাবেস (অটোমেটিক লোড করা)
// ==========================================
List<Map<String, dynamic>> allSurahs = [
  {
    'name': '১. আল-ফাতিহা',
    'info': 'মক্কী • ৭ আয়াত',
    'ayahs': [
      {'ar': 'بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ', 'bn': 'শুরু করছি আল্লাহর নামে যিনি পরম করুণাময়, অতি দয়ালু।'},
      {'ar': 'ٱلْحَمْدُ لِلَّهِ رَبِّ ٱلْعَـٰلَمِينَ', 'bn': 'যাবতীয় প্রশংসা আল্লাহ তাআলার যিনি সকল সৃষ্টি জগতের পালনকর্তা।'},
      {'ar': 'ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ', 'bn': 'যিনি নিতান্ত মেহেরবান ও দয়ালু।'},
      {'ar': 'مَـٰلِكِ يَوْمِ ٱلدِّينِ', 'bn': 'যিনি বিচার দিনের মালিক।'},
      {'ar': 'إِيَّاكَ نَعْبُدُ وَإِيَّاكَ نَسْتَعِينُ', 'bn': 'আমরা একমাত্র তোমারই ইবাদত করি এবং শুধুমাত্র তোমারই সাহায্য প্রার্থনা করি।'},
      {'ar': 'ٱهْدِنَا ٱلصِّرَٰطَ ٱلْمُسْتَقِيمَ', 'bn': 'আমাদেরকে সরল পথ দেখাও।'},
    ]
  },
  {
    'name': '২. আল-ইখলাস',
    'info': 'মক্কী • ৪ আয়াত',
    'ayahs': [
      {'ar': 'قُلْ هُوَ ٱللَّهُ أَحَدٌ', 'bn': 'বলুন, তিনি আল্লাহ, এক।'},
      {'ar': 'ٱللَّهُ ٱلصَّمَدُ', 'bn': 'আল্লাহ অমুখাপেক্ষী।'},
      {'ar': 'لَمْ يَلِدْ وَلَمْ يُولَدْ', 'bn': 'তিনি কাউকে জন্ম দেননি এবং কেউ তাকে জন্ম দেয়নি।'},
      {'ar': 'وَلَمْ يَكُن لَّهُۥ كُفُوًا أَحَدٌۢ', 'bn': 'এবং তার সমতুল্য কেউ নেই।'},
    ]
  },
  {
    'name': '৩. আল-ফালাক',
    'info': 'মাদানী • ৫ আয়াত',
    'ayahs': [
      {'ar': 'قُلْ أَعُوذُ بِرَبِّ ٱلْفَلَقِ', 'bn': 'বলুন, আমি আশ্রয় গ্রহণ করছি প্রভাতের পালনকর্তার।'},
      {'ar': 'مِن شَرِّ مَا خَلَقَ', 'bn': 'তিনি যা সৃষ্টি করেছেন, তার অনিষ্ট থেকে।'},
    ]
  },
  {
    'name': '৪. আন-নাস',
    'info': 'মাদানী • ৬ আয়াত',
    'ayahs': [
      {'ar': 'قُلْ أَعُوذُ بِرَبِّ ٱلنَّاسِ', 'bn': 'বলুন, আমি আশ্রয় গ্রহণ করছি মানুষের পালনকর্তার।'},
      {'ar': 'مَلِكِ ٱلنَّاسِ', 'bn': 'মানুষের অধিপতির।'},
    ]
  },
];

final List<Map<String, String>> names99 = [
  {'ar': 'الله', 'bn': 'আল্লাহ', 'meaning': 'সৃষ্টিকর্তা'},
  {'ar': 'الرَّحْمَنُ', 'bn': 'আর-রহমান', 'meaning': 'পরম দয়ালু'},
  {'ar': 'الرَّحِيمُ', 'bn': 'আর-রহীম', 'meaning': 'অতি মেহেরবান'},
  {'ar': 'الْمَلِكُ', 'bn': 'আল-মালিক', 'meaning': 'সর্বকর্তৃত্বময়'},
  {'ar': 'الْقُدُّوسُ', 'bn': 'আল-কুদ্দুস', 'meaning': 'নিষ্কলুষ'},
  {'ar': 'السَّلَامُ', 'bn': 'আস-সালাম', 'meaning': 'নিরাপত্তা দানকারী'},
];

// ==========================================
// ২. মেইন অ্যাপ (বইয়ের ডিজাইন সেটআপ)
// ==========================================
void main() {
  runApp(const MuslimAppPro());
}

class MuslimAppPro extends StatelessWidget {
  const MuslimAppPro({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Muslim Life Pro',
      theme: ThemeData(
        useMaterial3: true,
        // এই যে দেখুন, এখানে 'serif' দেওয়া আছে। এটাই বইয়ের ফন্ট।
        fontFamily: 'serif', 
        primaryColor: Colors.black, // মেইন কালার কালো
        scaffoldBackgroundColor: const Color(0xFFFFFBE6), // বইয়ের পাতার কালার (ক্রিম)
        appBarTheme: const AppBarTheme(
          backgroundColor: Colors.black, 
          foregroundColor: Colors.white,
          centerTitle: true,
          elevation: 0,
        ),
        textTheme: const TextTheme(
          bodyMedium: TextStyle(color: Colors.black, fontSize: 18),
          bodyLarge: TextStyle(color: Colors.black, fontSize: 20, fontWeight: FontWeight.bold),
        ),
      ),
      home: const HomeScreen(),
    );
  }
}

// ==========================================
// ৩. হোম স্ক্রিন (ঘড়ি + ফিচার)
// ==========================================
class HomeScreen extends StatefulWidget {
  const HomeScreen({super.key});
  @override
  State<HomeScreen> createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  String _time = "Loading...";
  String _date = "";
  Timer? _timer;

  @override
  void initState() {
    super.initState();
    _startClock();
  }

  void _startClock() {
    _timer = Timer.periodic(const Duration(seconds: 1), (timer) {
      final now = DateTime.now();
      setState(() {
        // সময় ফরম্যাট
        String period = now.hour >= 12 ? 'PM' : 'AM';
        int h = now.hour > 12 ? now.hour - 12 : (now.hour == 0 ? 12 : now.hour);
        String m = now.minute.toString().padLeft(2, '0');
        String s = now.second.toString().padLeft(2, '0');
        _time = "$h:$m:$s $period";

        // তারিখ ফরম্যাট
        List<String> months = ['জানু', 'ফেব্রু', 'মার্চ', 'এপ্রিল', 'মে', 'জুন', 'জুলাই', 'আগস্ট', 'সেপ্টে', 'অক্টো', 'নভে', 'ডিসে'];
        List<String> days = ['রবি', 'সোম', 'মঙ্গল', 'বুধ', 'বৃহঃ', 'শুক্র', 'শনি'];
        _date = "${days[now.weekday % 7]}, ${now.day} ${months[now.month - 1]} ${now.year}";
      });
    });
  }

  @override
  void dispose() {
    _timer?.cancel();
    super.dispose();
  }

  void _refresh() => setState(() {});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Muslim Life Pro"),
        actions: [
          IconButton(
            icon: const Icon(Icons.delete_outline),
            tooltip: "অ্যাডমিন প্যানেল",
            onPressed: () async {
              await Navigator.push(context, MaterialPageRoute(builder: (c) => const AdminScreen()));
              _refresh();
            },
          )
        ],
      ),
      body: Column(
        children: [
          // ঘড়ি ও তারিখের বক্স
          Container(
            width: double.infinity,
            padding: const EdgeInsets.all(20),
            decoration: const BoxDecoration(
              color: Colors.white,
              border: Border(bottom: BorderSide(color: Colors.black, width: 3)),
            ),
            child: Column(
              children: [
                Text(_time, style: const TextStyle(fontSize: 40, fontWeight: FontWeight.bold, color: Colors.black)),
                const SizedBox(height: 5),
                Text(_date, style: const TextStyle(fontSize: 18, color: Colors.black54)),
              ],
            ),
          ),
          
          Expanded(
            child: GridView.count(
              padding: const EdgeInsets.all(20),
              crossAxisCount: 2,
              crossAxisSpacing: 15,
              mainAxisSpacing: 15,
              childAspectRatio: 1.1,
              children: [
                _bookCard("আল-কোরআন", Icons.menu_book, () => Navigator.push(context, MaterialPageRoute(builder: (c) => const QuranListScreen()))),
                _bookCard("তসবিহ", Icons.touch_app, () => Navigator.push(context, MaterialPageRoute(builder: (c) => const TasbihScreen()))),
                _bookCard("৯৯ নাম", Icons.format_list_numbered, () => Navigator.push(context, MaterialPageRoute(builder: (c) => const NamesScreen()))),
                _bookCard("অন্যান্য", Icons.more_horiz, () => _msg(context)),
              ],
            ),
          ),
        ],
      ),
    );
  }

  Widget _bookCard(String title, IconData icon, VoidCallback onTap) {
    return GestureDetector(
      onTap: onTap,
      child: Container(
        decoration: BoxDecoration(
          color: Colors.white,
          border: Border.all(color: Colors.black, width: 2),
          borderRadius: BorderRadius.circular(5),
          boxShadow: const [BoxShadow(color: Colors.black26, offset: Offset(3, 3))],
        ),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(icon, size: 35, color: Colors.black),
            const SizedBox(height: 10),
            Text(title, style: const TextStyle(fontWeight: FontWeight.bold, fontSize: 18, color: Colors.black)),
          ],
        ),
      ),
    );
  }

  void _msg(BuildContext context) {
    ScaffoldMessenger.of(context).showSnackBar(const SnackBar(content: Text("শীঘ্রই আসছে...")));
  }
}

// ==========================================
// ৪. কোরআন পেজ (বই পড়ার মতো)
// ==========================================
class QuranListScreen extends StatelessWidget {
  const QuranListScreen({super.key});
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("সূচিপত্র")),
      body: allSurahs.isEmpty 
          ? const Center(child: Text("কোনো সূরা নেই")) 
          : ListView.separated(
              itemCount: allSurahs.length,
              separatorBuilder: (c, i) => const Divider(color: Colors.black45),
              itemBuilder: (context, index) {
                final surah = allSurahs[index];
                return ListTile(
                  title: Text(surah['name'], style: const TextStyle(fontSize: 22, fontWeight: FontWeight.bold)),
                  subtitle: Text(surah['info'], style: const TextStyle(fontSize: 14, color: Colors.black54)),
                  trailing: const Icon(Icons.arrow_forward, color: Colors.black),
                  onTap: () => Navigator.push(context, MaterialPageRoute(builder: (c) => SurahDetail(surah: surah))),
                );
              },
            ),
    );
  }
}

class SurahDetail extends StatelessWidget {
  final Map<String, dynamic> surah;
  const SurahDetail({super.key, required this.surah});

  @override
  Widget build(BuildContext context) {
    List ayahs = surah['ayahs'];
    return Scaffold(
      appBar: AppBar(title: Text(surah['name'])),
      body: ListView.builder(
        padding: const EdgeInsets.all(20),
        itemCount: ayahs.length + 1,
        itemBuilder: (context, index) {
          if (index == 0) {
            return Container(
              margin: const EdgeInsets.only(bottom: 30),
              padding: const EdgeInsets.all(10),
              decoration: BoxDecoration(border: Border.all(color: Colors.black12)),
              child: const Center(child: Text('بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ', style: TextStyle(fontSize: 26, fontWeight: FontWeight.bold))),
            );
          }
          final ayah = ayahs[index - 1];
          return Padding(
            padding: const EdgeInsets.only(bottom: 25),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: [
                Text(ayah['ar'], textAlign: TextAlign.right, style: const TextStyle(fontSize: 30, fontWeight: FontWeight.bold, height: 1.6)),
                const SizedBox(height: 10),
                Text(ayah['bn'], style: const TextStyle(fontSize: 18, height: 1.5, color: Colors.black87)),
                const Divider(color: Colors.black26, height: 30),
              ],
            ),
          );
        },
      ),
    );
  }
}

// ==========================================
// ৫. অ্যাডমিন প্যানেল (মালিকের জন্য)
// ==========================================
class AdminScreen extends StatefulWidget {
  const AdminScreen({super.key});
  @override
  State<AdminScreen> createState() => _AdminScreenState();
}

class _AdminScreenState extends State<AdminScreen> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("অ্যাডমিন প্যানেল")),
      body: Column(
        children: [
          Container(
            padding: const EdgeInsets.all(15),
            color: Colors.black12,
            child: const Text("ডিলিট বাটনে চাপ দিলে সূরাটি লিস্ট থেকে মুছে যাবে।", style: TextStyle(fontWeight: FontWeight.bold)),
          ),
          Expanded(
            child: ListView.separated(
              itemCount: allSurahs.length,
              separatorBuilder: (c, i) => const Divider(),
              itemBuilder: (context, index) {
                final item = allSurahs[index];
                return ListTile(
                  title: Text(item['name'], style: const TextStyle(fontWeight: FontWeight.bold)),
                  trailing: IconButton(
                    icon: const Icon(Icons.delete, color: Colors.red),
                    onPressed: () {
                      showDialog(
                        context: context,
                        builder: (ctx) => AlertDialog(
                          title: const Text("সতর্কতা"),
                          content: const Text("মুছে ফেলতে চান?"),
                          actions: [
                            TextButton(onPressed: () => Navigator.pop(ctx), child: const Text("না")),
                            TextButton(
                              onPressed: () {
                                setState(() => allSurahs.removeAt(index));
                                Navigator.pop(ctx);
                                ScaffoldMessenger.of(context).showSnackBar(const SnackBar(content: Text("মুছে ফেলা হয়েছে!")));
                              },
                              child: const Text("হ্যাঁ", style: TextStyle(color: Colors.red)),
                            ),
                          ],
                        ),
                      );
                    },
                  ),
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}

// ==========================================
// ৬. তসবিহ ও ৯৯ নাম
// ==========================================
class TasbihScreen extends StatefulWidget {
  const TasbihScreen({super.key});
  @override
  State<TasbihScreen> createState() => _TasbihScreenState();
}
class _TasbihScreenState extends State<TasbihScreen> {
  int count = 0;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("ডিজিটাল তসবিহ")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            GestureDetector(
              onTap: () => setState(() => count++),
              child: Container(
                height: 200, width: 200,
                decoration: BoxDecoration(
                  color: Colors.black,
                  shape: BoxShape.circle,
                  border: Border.all(color: Colors.white, width: 5),
                  boxShadow: const [BoxShadow(color: Colors.black38, blurRadius: 15)],
                ),
                child: Center(child: Text("$count", style: const TextStyle(fontSize: 70, fontWeight: FontWeight.bold, color: Colors.white))),
              ),
            ),
            const SizedBox(height: 30),
            OutlinedButton(
              onPressed: () => setState(() => count = 0),
              child: const Text("রিসেট", style: TextStyle(fontSize: 18, color: Colors.red)),
            )
          ],
        ),
      ),
    );
  }
}

class NamesScreen extends StatelessWidget {
  const NamesScreen({super.key});
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("৯৯ নাম")),
      body: ListView.separated(
        separatorBuilder: (c, i) => const Divider(),
        itemCount: names99.length,
        itemBuilder: (context, index) {
          final item = names99[index];
          return ListTile(
            leading: CircleAvatar(backgroundColor: Colors.black, child: Text("${index + 1}", style: const TextStyle(color: Colors.white))),
            title: Text(item['ar']!, style: const TextStyle(fontSize: 24, fontWeight: FontWeight.bold)),
            subtitle: Text("${item['bn']} - ${item['meaning']}"),
          );
        },
      ),
    );
  }
}
