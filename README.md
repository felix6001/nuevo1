proyecto1
import android.content.Intent
import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class ConfirmacionDatosActivity : AppCompatActivity() {
    private lateinit var tvNombre: TextView
    private lateinit var tvFechaNacimiento: TextView
    private lateinit var tvTelefono: TextView
    private lateinit var tvEmail: TextView
    private lateinit var tvDescripcion: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_confirmacion_datos)

        tvNombre = findViewById(R.id.tv_nombre)
        tvFechaNacimiento = findViewById(R.id.tv_fecha_nacimiento)
        tvTelefono = findViewById(R.id.tv_telefono)
        tvEmail = findViewById(R.id.tv_email)
        tvDescripcion = findViewById(R.id.tv_descripcion)

        val btnEditarDatos: Button = findViewById(R.id.btn_editar_datos)
        btnEditarDatos.setOnClickListener {
            val intent = Intent(this, ContactFormActivity::class.java)
            intent.putExtra("nombre", tvNombre.text.toString())
            intent.putExtra("fechaNacimiento", tvFechaNacimiento.text.toString())
            intent.putExtra("telefono", tvTelefono.text.toString())
            intent.putExtra("email", tvEmail.text.toString())
            intent.putExtra("descripcion", tvDescripcion.text.toString())
            startActivity(intent)
        }

        val nombre = intent.getStringExtra("nombre")
        val fechaNacimiento = intent.getStringExtra("fechaNacimiento")
        val telefono = intent.getStringExtra("telefono")
        val email = intent.getStringExtra("email")
        val descripcion = intent.getStringExtra("descripcion")

        tvNombre.text = nombre
        tvFechaNacimiento.text = fechaNacimiento
        tvTelefono.text = telefono
        tvEmail.text = email
        tvDescripcion.text = descripcion
    }
}
