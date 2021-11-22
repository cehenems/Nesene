# Nesene
nesne

class MainActivity : AppCompatActivity() {
    lateinit var etAd: EditText
    lateinit var rgCinsiyet: RadioGroup
    lateinit var rbKadin: RadioButton
    lateinit var rbErkek: RadioButton
    lateinit var cbKotlin: CheckBox
    lateinit var cbJava: CheckBox
    lateinit var cbC: CheckBox
    lateinit var cbCSharp: CheckBox
    lateinit var toggleButton: ToggleButton
    lateinit var switchSes: Switch
    lateinit var fab: ImageButton
    lateinit var btnDiger: Button

    override fun onStart() {
        super.onStart()
        Toast.makeText(this, "onStart çalıştı", Toast.LENGTH_LONG).show()
    }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        Toast.makeText(this, "onCreate çalıştı", Toast.LENGTH_LONG).show()
        etAd = findViewById(R.id.etAd)
        rgCinsiyet = findViewById(R.id.rgCinsiyet)
        rbKadin = findViewById(R.id.rbKadin)
        rbErkek = findViewById(R.id.rbErkek)
        cbKotlin = findViewById(R.id.cbKotlin)
        cbJava = findViewById(R.id.cbJava)
        cbC = findViewById(R.id.cbC)
        cbCSharp = findViewById(R.id.cbCSharp)
        toggleButton = findViewById(R.id.toggleButton)
        switchSes = findViewById(R.id.switchSes)
        fab = findViewById(R.id.FAB)
        btnDiger = findViewById(R.id.btnDiger)
        fab.setOnClickListener {
            finish()
            System.exit(0)
        }
        var cinsiyet = ""
        rgCinsiyet.setOnCheckedChangeListener { group, checkedId ->
            cinsiyet = if (R.id.rbKadin == checkedId) "Kadın" else "Erkek"
        }
        var kotlin=""
        cbKotlin.setOnCheckedChangeListener { buttonView, isChecked ->
            kotlin = if (isChecked) buttonView.text.toString() else ""
        }
        var java=""
        cbJava.setOnCheckedChangeListener { buttonView, isChecked ->
            java = if (isChecked) buttonView.text.toString() else ""
        }
        var c=""
        cbC.setOnCheckedChangeListener { buttonView, isChecked ->
            c = if (isChecked) buttonView.text.toString() else ""
        }
        var cSharp=""
        cbCSharp.setOnCheckedChangeListener { buttonView, isChecked ->
            cSharp = if (isChecked) buttonView.text.toString() else ""
        }

        btnDiger.setOnClickListener {
            var ad = etAd.text.toString()
            intent = Intent(this, SonucActivity::class.java)
            intent.putExtra("isim", ad)
            intent.putExtra("cinsiyet", cinsiyet)
            intent.putExtra("kotlin", kotlin)
            intent.putExtra("java", java)
            intent.putExtra("c", c)
            intent.putExtra("cSharp", cSharp)
            startActivity(intent)
        }
        switchSes.setOnCheckedChangeListener { buttonView, isChecked ->
            var msg = if (isChecked) "Açıldı" else "Kapandı"
            Toast.makeText(this, msg, Toast.LENGTH_LONG).show()
        }
        toggleButton.setOnCheckedChangeListener { buttonView, isChecked ->
            var msg = if (isChecked) "Açık" else "KApalı"
            Toast.makeText(this, msg, Toast.LENGTH_LONG).show()
        }
    }

    override fun onBackPressed() {
        Toast.makeText(this, "onBackPressed çalıştı", Toast.LENGTH_LONG).show()
        super.onBackPressed()
    }

    override fun onStop() {
        Toast.makeText(this, "onStop çalıştı", Toast.LENGTH_LONG).show()
        super.onStop()
    }

    override fun onDestroy() {
        Toast.makeText(this, "onDestroy çalıştı", Toast.LENGTH_LONG).show()
        super.onDestroy()
    }
}

