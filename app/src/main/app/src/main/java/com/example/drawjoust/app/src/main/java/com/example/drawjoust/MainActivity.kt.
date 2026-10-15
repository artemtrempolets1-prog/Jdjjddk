
package com.example.drawjoust

import android.app.Activity
import android.os.Bundle
import android.view.View
import android.view.WindowManager
import android.webkit.WebChromeClient
import android.webkit.WebView
import android.webkit.WebViewClient

class MainActivity : Activity() {

    private lateinit var game: WebView

    @Suppress("DEPRECATION")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        window.setFlags(
            WindowManager.LayoutParams.FLAG_FULLSCREEN,
            WindowManager.LayoutParams.FLAG_FULLSCREEN
        )

        game = WebView(this)
        game.settings.javaScriptEnabled = true
        game.settings.domStorageEnabled = true
        game.webViewClient = WebViewClient()
        game.webChromeClient = WebChromeClient()

        game.overScrollMode = View.OVER_SCROLL_NEVER
        game.keepScreenOn = true

        setContentView(game)

        if (savedInstanceState != null) {
            game.restoreState(savedInstanceState)
        } else {
            game.loadUrl("file:///android_asset/index.html")
        }

        hideSystemBars()
    }

    @Suppress("DEPRECATION")
    private fun hideSystemBars() {
        window.decorView.systemUiVisibility =
            (View.SYSTEM_UI_FLAG_FULLSCREEN
            or View.SYSTEM_UI_FLAG_HIDE_NAVIGATION
            or View.SYSTEM_UI_FLAG_IMMERSIVE_STICKY
            or View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
            or View.SYSTEM_UI_FLAG_LAYOUT_HIDE_NAVIGATION
            or View.SYSTEM_UI_FLAG_LAYOUT_STABLE)
    }

    override fun onSaveInstanceState(outState: Bundle) {
        game.saveState(outState)
        super.onSaveInstanceState(outState)
    }

    override fun onDestroy() {
        game.destroy()
        super.onDestroy()
    }

    @Deprecated("Deprecated in Android API")
    override fun onBackPressed() {
        if (::game.isInitialized && game.canGoBack()) {
            game.goBack()
        } else {
            super.onBackPressed()
        }
    }
}
