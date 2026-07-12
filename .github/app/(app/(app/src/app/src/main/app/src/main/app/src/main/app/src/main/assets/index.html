package com.miservicio.vpn;

import android.app.Activity;
import android.content.Intent;
import android.net.VpnService;
import android.os.Bundle;
import android.webkit.JavascriptInterface;
import android.webkit.WebSettings;
import android.webkit.WebView;
import android.widget.Toast;

public class MainActivity extends Activity {

    private WebView myWebView;
    private static final int VPN_REQUEST_CODE = 9915;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        myWebView = new WebView(this);
        setContentView(myWebView);

        WebSettings settings = myWebView.getSettings();
        settings.setJavaScriptEnabled(true);
        settings.setDomStorageEnabled(true); 

        // Creamos el puente de comunicación con tu HTML
        myWebView.addJavascriptInterface(new WebAppInterface(), "AndroidBridge");

        // Lee el archivo único de la carpeta de assets
        myWebView.loadUrl("file:///android_asset/index.html");
    }

    public class WebAppInterface {
        @JavascriptInterface
        public void iniciarTunel(String jsonDatos) {
            // Lanza el cuadro de diálogo nativo pidiendo permiso para la VPN
            Intent intent = VpnService.prepare(MainActivity.this);
            if (intent != null) {
                startActivityForResult(intent, VPN_REQUEST_CODE);
            } else {
                activarMotorVpn();
            }
        }
    }

    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (requestCode == VPN_REQUEST_CODE && resultCode == RESULT_OK) {
            activarMotorVpn();
        } else {
            Toast.makeText(this, "Permiso de red denegado", Toast.LENGTH_SHORT).show();
            ejecutarJsEnWeb("confirmacionDesdeAndroid(false)");
        }
    }

    private void activarMotorVpn() {
        runOnUiThread(new Runnable() {
            @Override
            public void run() {
                // Le avisa a tu HTML que el permiso fue concedido y cambia el botón a verde
                ejecutarJsEnWeb("confirmacionDesdeAndroid(true)");
            }
        });
    }

    private void ejecutarJsEnWeb(String script) {
        myWebView.evaluateJavascript(script, null);
    }
}
