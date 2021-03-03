# Extensions-Methods
Extensions Methods are kind of helper methods merged into custom or default data types or classes or any libary.

### -Simple Extensions  UI


        fun View.setRowWidth() {
            val layoutParam = RecyclerView.LayoutParams(
                ViewGroup.LayoutParams.MATCH_PARENT,
                ViewGroup.LayoutParams.WRAP_CONTENT
            )
            this.layoutParams = layoutParam
            this.requestLayout()

        }

        fun TextView.maxLength(value: Int) {
            this.filters = arrayOf<InputFilter>(InputFilter.LengthFilter(value))
        }


        fun ImageView.loadImage(url: String?) {

            if (url.isNullOrEmpty()) return

            val builder = LazyHeaders.Builder()

            val glideUrl = GlideUrl(url, builder.build())

            val requestOptions = RequestOptions()
                .diskCacheStrategy(DiskCacheStrategy.ALL)
                .priority(Priority.HIGH)

            Glide.with(this.context)
                .setDefaultRequestOptions(requestOptions)
                .load(glideUrl)
                .into(this)
        }

        fun View.expand() {
            visibility = View.VISIBLE
            val animate = TranslateAnimation(0f, 0f, -height.toFloat(), 0f)
            animate.duration = 200
            animate.fillAfter = true
            startAnimation(animate)
        }

        fun View.collapse() {
            val animate = TranslateAnimation(0f, 0f, 0f, -height.toFloat())
            animate.duration = 200
            animate.fillAfter = true
            startAnimation(animate)
        }


        fun View.setBackDrawableGroundTint(color: Int) {

            DrawableCompat.setTint(
                this.background,
                ContextCompat.getColor(this.context, color)
            )

        }

        fun ImageView.setResourceDrawableGroundTint(color: Int) {

            DrawableCompat.setTint(
                this.drawable,
                ContextCompat.getColor(this.context, color)
            )

        }


        fun AppCompatTextView.setTextColorExtension(color: Int) {

            this.setTextColor(
                ContextCompat.getColor(
                    this.context,
                    color
                )
            )

        }


        fun AppCompatTextView.drawUnderLine() {
            val text = SpannableString(this.text.toString())
            text.setSpan(UnderlineSpan(), 0, text.length, 0)
            this.text = text
        }

        fun ViewGroup.setLayoutChangingTransition() {
            this.layoutTransition =
                LayoutTransition()
            this.layoutTransition.enableTransitionType(LayoutTransition.CHANGING)
        }



      
            val label: SpannedString = buildSpannedString {

                append("Rs. ")

                bold { //here we are adding bold font to string
                    append("Rs. ${5,000.00}")
                }
                append(" required")
            }
