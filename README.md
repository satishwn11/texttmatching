   val words = arrayOf("apple", "banana", "mango", "orange") // ✅ Valid words ka array

        editText.addTextChangedListener(object : TextWatcher {
            override fun beforeTextChanged(s: CharSequence?, start: Int, count: Int, after: Int) {}

            override fun onTextChanged(s: CharSequence?, start: Int, before: Int, count: Int) {
                val inputText = s?.toString()?.trim() ?: ""  // 🔹 User jo likh raha hai

                if (inputText.isEmpty()) {
                    textView.text = "" // Agar kuch likha hi nahi to blank rahe
                    return
                }

                val isMatching = words.any { it.startsWith(inputText, ignoreCase = true) }

                if (isMatching) {
                    textView.text = "✅ Correct"
                    textView.setTextColor(Color.GREEN)
                } else {
                    textView.text = "❌ Incorrect"
                    textView.setTextColor(Color.RED)
                }
            }

            override fun afterTextChanged(s: Editable?) {}
        })
