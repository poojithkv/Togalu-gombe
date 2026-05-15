package com.example.togalugombe

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.lazy.LazyColumn
import androidx.compose.foundation.lazy.items
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp

data class Story(
    val title: String,
    val description: String
)

class MainActivity : ComponentActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContent {
            TogaluGombeApp()
        }
    }
}

@Composable
fun TogaluGombeApp() {

    val stories = listOf(
        Story(
            "Ramayana",
            "Traditional shadow puppet story from Ramayana."
        ),
        Story(
            "Mahabharata",
            "Epic storytelling performance using leather puppets."
        ),
        Story(
            "Folk Legends",
            "Ancient Karnataka cultural folk tales."
        )
    )

    MaterialTheme {

        Column(
            modifier = Modifier
                .fillMaxSize()
                .padding(16.dp)
        ) {

            Text(
                text = "Togalu-Gombe",
                style = MaterialTheme.typography.headlineMedium
            )

            Spacer(modifier = Modifier.height(8.dp))

            Text(
                text = "Digital Shadow Theater Companion"
            )

            Spacer(modifier = Modifier.height(20.dp))

            LazyColumn {

                items(stories) { story ->

                    Card(
                        modifier = Modifier
                            .fillMaxWidth()
                            .padding(8.dp)
                    ) {

                        Column(
                            modifier = Modifier.padding(16.dp)
                        ) {

                            Text(
                                text = story.title,
                                style = MaterialTheme.typography.titleLarge
                            )

                            Spacer(modifier = Modifier.height(8.dp))

                            Text(text = story.description)

                            Spacer(modifier = Modifier.height(12.dp))

                            Button(
                                onClick = { }
                            ) {
                                Text("View Story")
                            }
                        }
                    }
                }
            }
        }
    }
}
