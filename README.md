Clone this repo or copy https://github.com/geoff-huang/HiltTemplate/commit/cefb02e6d1ac02401cb2d97af20812c351136074

Sample code for providing Preferences DataStore
```
@Module
@InstallIn(SingletonComponent::class)
object TestModule {

    @Provides
    @Singleton
    fun provideTestRepository(
        prefsDataStore: DataStore<Preferences>
    ): TestRepository {
        return TestRepositoryImpl(prefsDataStore)
    }

    @Provides
    @Singleton
    fun providePreferencesDataStore(
        @ApplicationContext context: Context
    ): DataStore<Preferences> {
        return PreferenceDataStoreFactory.create {
            File(context.filesDir, "test.preferences_pb")
        }
    }
}
```
